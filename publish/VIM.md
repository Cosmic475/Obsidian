
Allows us to write code or edit text files on remote linux systems

~~~
Parzii@htb[/htb]$ vim /etc/hosts
~~~

To open the file

Creating a new file is a simple as vim followed be the new file name

Files open in read only mode, which we can change with "i" allowing us to to into insert mode and use the arrow keys for navigation


Esc returns us back to normal mode, where the following shortcuts work

|Command|Description|
|---|---|
|`x`|Cut character|
|`dw`|Cut word|
|`dd`|Cut full line|
|`yw`|Copy word|
|`yy`|Copy full line|
|`p`|Paste|

Tip: We can multiply any command to run multiple times by adding a number before it. For example, '4yw' would copy 4 words instead of one, and so on.


Press : to go into command mode to save a file

|   |   |
|---|---|
|`:1`|Go to line number 1.|
|`:w`|Write the file, save|
|`:q`|Quit|
|`:q!`|Quit without saving|
|`:wq`|Write and quit|