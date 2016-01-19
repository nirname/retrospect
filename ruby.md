# Ruby

## Strings

**squish**

Remove new lines and extra spaces

    <<-MSG.squish
      Hello
      world
    MSG

    # => "Hello world"

**strip_heredoc** (Rails only)

Remove initial indentation

    <<-MSG.strip_heredoc
      Hello
        world
    MSG

    # => "Hello\n  world"
