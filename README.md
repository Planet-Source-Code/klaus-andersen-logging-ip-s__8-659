﻿<div align="center">

## Logging IP's


</div>

### Description

This is basically an IP-logger, which keeps a record of if a person with that ip has been there before.

This is great for counters which will prevent refresh-increasing the count. Just place the counter-events witin the correct function. The Welcome-part and not the Welcome back.
 
### More Info
 
Basic php knowledge. But clip and paste will work just as good.

The main function returns true and false, depending on if the curren ip of the browser is in the file.

There might be bugs, I havent tested it enough, if there is a flaw please post a reply.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Klaus Andersen](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/klaus-andersen.md)
**Level**          |Beginner
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |PHP 3\.0, PHP 4\.0
**Category**       |[Server Side](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/server-side__8-31.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/klaus-andersen-logging-ip-s__8-659/archive/master.zip)





### Source Code

```
<?php
if (!$filename) { //check if it is in the dir
  $filename = "default.txt"; //the default file
if (file_exists("$filename")) {
//echo "The file exists.<br>";
//early experiments
}
else {
$fp = fopen($filename,"a+");
fputs($fp,"999.555.444.21\n");
//999.555.444.21
//just so that there is something in the file
//at the beginning
fclose($fp);
}
}
//the main code
function ticker($filename,$remoted,$mode,$stuff) {
  $fp = fopen("checklist.txt","w+");
  $filename2 = "checklist.txt";
//the checklist
//is just a base of comparison
// i found that comparing $REMOTE_ADDR and the
// other file had some flaws
// so writing a new one worked best with the
// same content, it was probably because of the
// linefeed character
  fputs($fp,"$remoted\n");
  fclose($fp);
  $check_var = 0;
  $inlines = file($filename2);
  $inline = file($filename);
  $number_of_lines = count($inline);
  for($x = 0; $x <= $number_of_lines ;$x++){
  echo "$inlines[0]";
  echo "<br>$inline[$x]";
if ($inlines[0] == $inline[$x]) {
$check_var = 1;
}
}
return $check_var;
}
if (!ticker($filename,$REMOTE_ADDR,null,null)) {
$fp = fopen($filename,"a+");
fputs($fp,"$REMOTE_ADDR\n");
fclose($fp);
echo "WELCOME FFS!";
}
else {
echo "WELCOME BACK FFS!";
}
  ?>
```

