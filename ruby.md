# Ruby

## Strings

**squish**

Remove new lines and extra spaces

```ruby
<<-MSG.squish
  Hello
  world
MSG

# => "Hello world"
```

**strip_heredoc** (Rails only)

Remove initial indentation

```ruby
<<-MSG.strip_heredoc
  Hello
    world
MSG

# => "Hello\n  world"
```
