# Shell Basics

The `$` symbol in front of the word indicates that it is a shell variable.

---

It's `cd ..` not `cd..`.  
If the director name has space in it use `''`

---

`;` lets you write 2 commands on the same line.  Shell would run them in order. 

    cd .. ; ls

---

The command ls `Dropbox/../Dropbox` works the same as `ls Dropbox` because `..` represents the parent directory. When you use `..` in a file path, it refers to the directory one level above the current directory.

In this case, `Dropbox/../Dropbox` is equivalent to `Dropbox/..` which is the parent directory of the Dropbox directory. So, when you run `ls Dropbox/../Dropbox`, it is essentially the same as running `ls Dropbox`, as both commands list the contents of the Dropbox directory.

---

`ls ~` is a shortcut, which stands for my home directory.

---

The > symbol is a redirection operator that directs the output of the echo 
command into a file.

`echo 'My Project' > README` creates a file "README" and adds "My 
Project" in it. 

---

The touch command is a simple way to create an empty file.

	touch filename

---

	nano filename

This opens the nano editor with a new file named filename. You can then 
type your content, save it with Ctrl+o (the letter o not zero), and exit 
with Ctrl+x.

Use Ctrl + K to cut a line and Ctrl + U to uncut (paste) a line.

---

The mv command not only moves files but also allows you to rename them by 
specifying the new name.

	mv current_filename new_filename

---

`mv` will overwrite it without any warning. Use the `-i` option to be prompted before overwriting:

	mv -i oldfile.txt newfile.txt

---

It’s often a good idea to create a backup before renaming important files.

	cp oldfile.txt oldfile_backup.txt  
	mv oldfile.txt newfile.txt

---

	mkdir -p parent/child/grandchild

This will create the parent directory, the child directory inside parent, and the grandchild directory inside child if they do not already exist.
