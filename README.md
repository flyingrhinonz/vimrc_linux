**vimrc** is the config file that controls how vim behaves, interacts and displays output.
In most distros you'll get a preconfigured vimrc file that represents the distro's point of view on how simple or complicated the setup should be - it is usually a compromise that vim look and behave traditionally rather than expose advanced and powerful features.

Once you've learnt the basics of vim, you'll realize how powerful vim really is and you will start to expect it to behave in a way that makes you more productive.
This is where my custom **vimrc** file comes in - replace or augment your file with this one to take advantage of vim features that are normally hidden behind non-default settings.

You can use it in two ways:
* Replace your:  **vimrc.local**  with the one on this page and all is good. You'll be using the:  **vimrc.local.ken**  file I supplied, probably saved as:  **/etc/vim/vimrc.local**  (debian-based distros), or something similar, based upon your own distro's requirements.
* Alternatively you may wish to keep your regular config untouched (especially in multi user environments where other users are not expecting such a powerful vim), and enable it only for yourself. This is the scenario I will describe next and explain how to set it up.


The file that is really required is:   **vimrc.local.ken**   - this is the custom vimrc file. Place it alongside your normal vimrc file, normally somewhere in:  **/etc/**  or:  **/etc/vim/** .
Then we need: **vim-kenmode**   -  which is sourced before you use vim.
Finally, we need extra lines in:  **/etc/vim**  (or:  **vimrc**  or any other vim config file your system uses) that knows how to handle the custom file.
Basically vim loads its config files and at the end of the load process it reaches the commands that instruct it to load the custom:   **vimrc.local.ken**   file.


In a directory of your choice (normally your home dir), place this file:  **vim-kenmode**   .
Then make it executable:  **chmod +x vim-kenmode**  .


Edit the:  **vimrc**  or: **vimrc.local**  file  (you'll find it under **/etc/**  or  **/etc/vim/** ) and add these lines at the end:


```
if exists("$MYCUSTOMVIM")
  if filereadable("/etc/vimrc.local.".$MYCUSTOMVIM)
    source /etc/vimrc.local.$MYCUSTOMVIM
  endif
endif
```


Then simply source your vim file with the following command:  **. vim-kenmode**  and enjoy productive editing.


Color codes for cterm can be found [here](https://upload.wikimedia.org/wikipedia/commons/thumb/1/15/Xterm_256color_chart.svg/1404px-Xterm_256color_chart.svg.png) . Respect and thanks to its creator for making it available.


