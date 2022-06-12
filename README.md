# scripts.inc to scripts.pory converter

--------
```
#!/bin/bash

for directory in data/maps/* ; do

	pory_exists=$(find $directory -name $"scripts.pory" | wc -l)

	if [[ $pory_exists -eq 0 ]]; 

	then

		inc_exists=$(find $directory -name $"scripts.inc" | wc -l)

		if [[ $inc_exists -ne 0 ]]; 

		then

			echo "Converting: $directory/scripts.inc"

			touch "$directory/scripts.pory"

			echo 'raw `' >> "$directory/scripts.pory"

			cat "$directory/scripts.inc" >> "$directory/scripts.pory"

			echo '`' >> "$directory/scripts.pory"

		fi

	fi

	done
```

This is a simple bash shell script that when ran in the main pokeemerald folder, will convert all scripts.inc files in every map in data/maps/, into the appropriate scripts.pory file by copying the contents of the scripts.inc file into raw \`\` tags. It will skip any directory that already has a scripts.pory file as to not overwrite any scripts that you already converted to the .pory extension. 

Once the bash file is in your pokeemerald directory, simply navigate to your folder in WSL and type:

`./inc_to_pory`

And it will run the shell script and convert all your files. You may need to give it permissions with chmod 777 inc_to_pory if it doesn't work at first and make sure its in the right directory. 

-----

Making Changes

If you want to get rid of the console output, remove the line that says 'echo "Converting....." 

If you want to call the command from other places change the directory in the for loop to match the directory you want to choose. For example if you wanted to run it from outside the decomp you would change data/maps/* to pokeemerald/data/maps/*
