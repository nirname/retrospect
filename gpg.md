# GPG

## Статьи

* <https://robots.thoughtbot.com/pgp-and-you>
* <https://www.opennet.ru/base/sec/gpg_crypt.txt.html>
* <https://gpgtools.org/> - удобная штука для мака, которая решает все проблемы

## Установка

```bash
brew install gpg2    # инсталяция на маке и я сделал у себя alias gpg=gpg2 (на убунте скорее всего уже установлено)

gpg --gen-key                                                        # создать ключ
gpg --armor --export me@example.com > me@example.com_pub             # сохранить свой публичный ключ в файл
gpg --armor --export-secret-key me@example.com > me@example.com_sec  # сохранить свой приватный ключ в файл

gpg --import me@example.com_pub                                # добавить свой публичный ключ на другой машине
gpg --allow-secret-key-import --import me@example.com_sec      # добавить свой публичный ключ на другой машине

gpg --list-keys # посмотреть список ключей
```

Добавление ключей других людей вручную:

```bash
gpg --import person@example.com_pub                    # добавить у себя публичный ключ другого человека
# рекомендуется пометить этот ключ как trusted
# если не сделать этого, то работать тоже можно будет, но нужно будет лишний раз жать y
gpg --edit-key person@example.com_pub # далее trust<enter>5<enter>y
```

## Использование:

### Отправить шифрованный файл человеку

```bash
gpg -r person@example.com -a -e some-file
# получается файл some-file.asc, который можно отправить любым публичным каналом (почта, слек и тд)
```

### Расшифровать файл, который пришел к вам

```bash
gpg --decrypt-files some-file.asc
```
