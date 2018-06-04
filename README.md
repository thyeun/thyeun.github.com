# Yeun's Studios

## Requirements (for testing)

- [Jekyll] 1.4.3+
- [RDiscount]

## Setup

### OSX
`$ ./install-mac.sh`

## How to write a post
1. _post create a post using [Markdown] with the file name.[yyyy-mm-dd-title.md]
2. Commit to push the contents into the main directory.

        $ git add -A
        $ git commit -m "Add a post..."
        $ git push

## Testing

        $ jekyll serve

## Writing Tips
1. _post In the files within a folder on YAML Front Matter block <code>author</code> and <code>You pocket the author-email</code>. <code>author</code> is created by people, and <code>author-email</code> can be entered on the author e-mail, so additional information on the actual post will take the mail link. (<Code>author</code> If no link only).
2. Also _post in the files within a folder on YAML Front Matter block <code>publish</code> it is the <code>If you enter false</code> You can not view the post. Only post information will pop up this list, brooding post Coming Soon. The end of the draft work <code>publish</code> to <code>true</code>, or just with <code>will be cleared to please publish</code> itself.

  [Jekyll]: http://jekyllrb.com
  [Markdown]: http://daringfireball.net/projects/markdown/
  [RDiscount]: http://dafoster.net/projects/rdiscount/
