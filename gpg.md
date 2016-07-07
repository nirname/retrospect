# GPG

Статьи:

* https://robots.thoughtbot.com/pgp-and-you
* https://www.opennet.ru/base/sec/gpg_crypt.txt.html
* https://gpgtools.org/ - удобная штука для мака, которая решает все проблемы

Установка:

    brew install gpg2    # инсталяция на маке и я сделал у себя alias gpg=gpg2 (на убунте скорее всего уже установлено)

    gpg --gen-key                                                        # создать ключ
    gpg --armor --export vakhov@uchi.ru > vakhov@uchi.ru_pub             # сохранить свой публичный ключ в файл
    gpg --armor --export-secret-key vakhov@uchi.ru > vakhov@uchi.ru_sec  # сохранить свой приватный ключ в файл

    gpg --import vakhov@uchi.ru_pub                                # добавить свой публичный ключ на другой машине
    gpg --allow-secret-key-import --import vakhov@uchi.ru_sec      # добавить свой публичный ключ на другой машине

    gpg --list-keys # посмотреть список ключей

Добавление ключей других людей вручную:

    gpg --import kot@uchi.ru_pub                    # добавить у себя публичный ключ другого человека (или кота)
    # рекомендуется пометить этот ключ как trusted
    # если не сделать этого, то работать тоже можно будет, но нужно будет лишний раз жать y
    gpg --edit-key kot@uchi.ru # далее trust<enter>5<enter>y
    Использование:

# отправить шифрованный файл человеку

    gpg -r kot@uchi.ru -a -e some-file # получается файл some-file.asc,
                                   # который можно отправить любым публичным каналом (почта, слек и тд)

# расшифровать файл, который пришел к вам

    gpg --decrypt-files some-file.asc

Ура!
