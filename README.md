# A little plan9 Command to read github blobs

Copy this command to $home/bin/rc and call

	github OPTIONS {USER/REPOSITORY} [FILE]

The command simply translates the arguments into

	hget https://github.com/$repo/blob/$branch/$file|sed -ne '/<article/,/<\/article/p'|htmlfmt

where

- repo = USER/REPOSITORY	# actually the first non-option argument (mandatory)
- file = FILE				# actually the second non-option argument (default = README.md)
- branch = -b|--branch arg	# the argument of the option `-b` or the long option `--branch` (default = master)

Happy githubbing!

