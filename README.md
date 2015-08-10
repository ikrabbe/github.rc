# A little plan9 Command to read github blobs

Copy this command to $home/bin/rc and call

	github OPTIONS {USER/REPOSITORY} [FILE]

The command simply translates the arguments into

	hget https://github.com/$repo/$mode/$branch/$file

. For `mode=blob` mode I use 

	hget https://github.com/$repo/$mode/$branch/$file|sed -ne '/<article/,/<\/article/p'|htmlfmt

where

- repo = USER/REPOSITORY	# actually the first non-option argument (mandatory)
- file = FILE				# actually the second non-option argument (default = README.md)
- branch = -b|--branch arg	# the argument of the option `-b` or the long option `--branch` (default = master)
- mode = --blob			# mode=blob for articles (as README.md). mode=raw is the default

## Example

To read the README.md of this repository you simply use

	github ikrabbe/github.rc

, to show the rc command itself you can use

	github ikrabbe/github.rc github

and finally to install the command into your $home/bin/rc you can do

	github ikrabbe/github.rc github > bin/rc/github; chmod 755 bin/rc/github

(of course you would need the github command before you can install it, in this example ;)).

Happy githubbing!

