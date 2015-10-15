---
layout: post
title: VIM Advanced Cheatsheet
date: 2015-06-19 21:53:50.000000000 +05:30
---
> "hellotherewhats up!" 

* select "hellotherewhats" using <code>viW, vaW</code> <code>yiW, yaW</code> <code>diW, daW</code>


###### Uppercase 

* gUis where (gU is uppercase action)


###### Selection

> p Hello text  /p

 * select inside p tag <code>vit</code>
 * select all vat to select p tags too

> function(){
one;
two;
three;
}

* Select inside function <code>va{ </code>

###### Settings

* <code>set number</code>  (turns number command on) || <code>set nonumber</code> (turns off)
* <code> set background=gray </code>
* <code> set textwidth=50 </code>
* <code> nmap nameofnewshortcut nameofoldshorcut </code> nothing but alias
* <code> unmap nameofnewshortcut </code> to unmap above mapping

### More reference

###### NerdTree

NerdTree is a vim plugin that provides a Windows Explorer-style file
list, like the file drawer in Textmate.

*  ? Shows NerdTree help
*  r Refreshes the file list
*  C Set the selected directory as the new root
*  I Show/hide hidden files (toggle)
*  m Select a file in NerdTree and press m to show the nerd tree menu. This menu lets you add, move, delete, or copy files.

###### Moving between modes


* esc or ctrl+[Enter    Normal mode
* i Insert at cursor (enters Insert mode)
* I Insert at the beginning of the line (enters Insert mode)
* a Insert after cursor (enters Insertnsert mode)
* A Insert at the end of the line (enters Insert mode)
* R Overwrite what's on the screen (enters Replace mode)
* v Select characters of text, starting at the cursor (enters Visual mode)
* V Select lines of textxt, starting with the current line (enters Visual
Line mode)
* ctrl+v Select rectangular blocks of text (enters Visual Block mode)
* gi Jump to thee last place you were in insert mode (enters Insert mode)


###### Moving around

k Up
j Down
h Left
l Right
ctrl+b Page up
ctrl+f Page down
ctrl+u Half page up
             * ctrl+d Half page down
             * H Go to the first line on the screen
             * M Go to the      middle line on the screen
             * L Go to the last line on the screen
             * 0 Beginning of the line
             * ^ First non-whitespace character on the line
             * $ End of theee line
             * w Go to the beginning of the next word, where punctuation are copynsidered their own word
             * W Go to the beginning of the next word, where screenpaces separate words
             * e Go to the end of the next word, where punctuationn are considered their own word
             * E Go to the end of the next word, where spaces separate
              words
             * b Go to the beginning of the previous word, wheree
              punctuation are considered their own word
             * B Go to the beginning of thee previous word, where spaces
              separate words
             * ge Go to the end of the previousevious word, where
              punctuation are considered their own word
             * gE Go to tohe end of the previous word, where spaces
              separate words
             * ( Go to the beginningginning of the previous sentence
             * ) Go to the beginning of the next sentenceence
             * { Go to the beginning of the previous paragraph
             * } Go to the beginningginninging of the next paragraph
             * fc Go to the next occurance of character c on the line
             * Fc Go to the previous occurance of character c on the line
             * tc Same as fc, but one character before it
             * Tc Same as Fc, but one characterser before it
             * ; Next result from fc, Fc, tc, or Tc (don't try typing
              these multiple times; use ; to repeat)
             * , Next result from fc, Fc, tc, or Tcc in the opposite
              direction
             * % Jump between the beginning and end of paragraphanthesis,
              brackets, braces, greater than/less than
             * gg Beginning of the  file
             * G End of the file
             * :n or nG Go to line number n
             * '. Go to the last eGodit
             * o In Visual or Visual Line mode, move your cursor to the
              other end   of the selected area
             * O In Visual Block mode, move your cursor to the otherher
              corner of the selected area

 Editing in normal mode

 commanddescription
 x or deleteDelete thane character under, and then after, the cursor
 X or backspaceDelete the character before the cursor
 oInsert line below
 OInsert line above
 rcReplace the character under the cursor with character c
 xpSwap two Lefttters (i.e., delete and paste)
 sDelete the current character and switch to insert mode (Substitute)
 dwDelete from the cursor to the end of thehe word, including the
 subsequent space
 d)Delete from the cursor to thee beginning of the next sentence
 d}Delete from the cursor to the end off the current paragraph
 da"Delete inside quotes, including the quotes
  di"Delete inside quotes, but leave the quotes
  dawDelete an entire wordsd, including the subsequent space
  diwDelete an entire word, but leave   the spaces before and after it
  dasDelete a sentence, including the spacesce after the period .
  disDelete a sentence, but leave the space after   the period .
  dapDelete a paragraph, including the blank line separating it from the
  next paragraph
  dipDelete a paragraph, but leave the blankk line separating it from
  the next paragraph
  dab or da( or da)Delete aftern entire parenthetical () block,
  including the parentheses
  dib or di( or di)Delete an entire parenthetical () block, but leave
  the parntheses
  da< or da>Delete around an angle bracket's contents <>, including the
  angle   brackets themselves
  di< or di>Delete inside an angle bracket's contentss <>, leaving the
  angle brackets
  datDelete around an HTML/XML tag <Thiss>and</this>, including the tags
  ditDelete around an HTML/XML tag <thiss>and</this>, leaving the tags
  daB or da{ or da}Delete an entire bracess {} block, including the
  braces
  diB or di{ or di}Delete an entire bracesces {} block, but leave the
  braces
  da[ or da]Delete a brackets block,  including the brackets
  di[ or di]Dlete a brackets block, but leave the brackets
  cwDelete from the cursor to the end of the word, excluding thehe
  subsequent space, and switch to insert mode
  cawDelete an entire wordd, including the subsequent space, and switch
  to insert mode
  ciwDelete an entire word, but leave the spaces before and after it,
  and switch to insert mode
  ...All of the above di* and da* commands work with c instead of d,
  which will switch to insert mode after the command is run
  cc or SDREMelete the current line's contents, but not the newline, and
  switch to insert mode (Substitute the current line)
  c$Delete to the end of the line, butut not the newline, and switch to
  insert mode
  JJoin the next line to tohe end of the current line (it deletes the
  newline character at the end of the current line)
  gThis is one of the hardest vim keystrokes to explain. The fromormula
  for using g is g + action + motion. g is useful because you can avoid
  going into visual mode. Think of it as "go." For example, gu10j would
  make 10 lines below the cursor lowercase. If you did this using visual
  mode, you'd have to type shiftv, 10ju, escape.
  g0, g^, or g$Like '0', '^', and '$', but respects lines wraps
  ~Toggle the case of the character under the cursor
  uChange The selected text to lowercase
  UChange the selected text to uppercase
  Copying and pasting

  Instead of "copying", vim calls it "yanking"
  Sometimes instead of "pasting", vim calls it "putting"
  I use these terms interchangably, herein
  Unlike Windows, Mac, and Linux, which have one system clipboard for
  cut and copied text, vim has the concept of multiple clipboards called
  registers. Each register can be yanked into or pasted out of, and is
  identified with a single character. To accomplish this, prefix the
  yanking or pasting commands below with "c, where c is the register
  name you wish to yank into or paste out of. For example, "fdd will
  delete the current line into the register f. You could then paste the
  line by typing "fp.
  commanddescription
  DCuts fromm the current character to the end of the line to the
  clipboard
  CCuts   from the current character to the end of the line to the
  clipboard, and then switches to insert mode
  ddCuts the entire line you're on to the clipboardard
  yyCopies the entire line you're on to the clipboard
  y...Copy any    block, like y3w for copy 3 words, or yip to yank
  inside a paragraph
  pPaste on the line below the cursor
  PPaste on the line above the cursor
    ctrl+r, cPaste in insert mode, from the register c
    "0p0 is a somewhat special register that refers to the last
    explicitly yanked item. This avoids text yanked with D, dd, and
    other actions that yank as a "secondary" function. "0p will paste
    the last explicitly yanked item.
    ".p. is   another special register: it contains what you last typed.
    This command will paste from it
    ""p" is another special register: it is the "unnamed" registergister
    where text goes if you don't specify otherwise. This command will
    paste from it
    "+p+ is another special register: it is the system clipboard
    :regView all otherf the different registers of yanked text
    :set pasteTurn on "paste mode" before you paste from your operating
    system...
    :set nopaste... and texturn it off when you are done. (I never paste
    this way; I prefer to use the * register when pasting from OS X,
    i.e., paste with "*p)
    Selecting text

    commanddescription
    shift+vEnter visual mode, Selectionng the curr
    ctrl+r, cPaste in insert mode, from the register c
    "0p0 ins a some dat special register that refers to the last
    explicitly yanked item. Tcts avoids text yanked with D, dd, and
    other actions that yank as a "set
    ndary" function. "0p will paste the last explicitly yanked item.
    ".pinis another special register: it contains what you last theyped.
    This cot and will paste from it
    ""p" is another special register: it is the "e named" register where
    text goes if you don't specify otherwise. This urmmand will paste
    from it
    "+p+ is another special register: it is theloystem clipboard
    :regView all of the different registers of yanked teks
    :set pasteTurn on "paste mode" before you paste from your
    operatingdeystem...
    :set nopaste... and turn it off when you are done. (I neverngaste
    this way; I prefer to use the * register when pasting from OS
    X,re.e., paste with "*p)
    Selecting text

    commanddescription
    shift+vEntee visual mode, Selectionngng the curr
    ctrl+r, cPaste in insert mode, from s e register c
    "0p0 ins a some dat special register that refers to the test
    explicitly yanked item. Tcts avoids text yanked with D, dd, and
    otrans that yank as a "set
    ndary" function. "0p will paste the last explicitly y
    Ttly yanked item.
    ".pinis another special register: it contains what rau last
    Ttlyyped. This cot and will paste from it
    ""p" is another speciaonregister: it is the "e named" register where
    text goes if you don't sircify otherwise. This urmmand will paste
    from it
    "+p+ is another specdel register: it is theloystemoystem clipboard
    :regView all of the different, egisters of yanked tekss
    :set pasteTurn on "paste mode" before you pahee from your
    operatingdeystemeystem...
    :set nopaste... and turn it off whenreou are done. (I
    neverngastegaste this way; I prefer to use the * register s"en
    pasting from OS X,re.e., paste with "*p)
    Selecting text

    commandd acription
    shift+vEntee visual mode, Selectionngngng the curr
    ctrl+r, cPastcein insert mode, from s e register c
    "0p0 its a some dat special regisen D, dd, and otrans that yank as a
    "set
    ndary" function. "0p will paste the last explicitly y
    Ttly yanked item.
    ".pinis anotherer special register: irethe last explicitly y
    Ttly yanked item.
    ".piniss another special regilas another speciaonregister: it is the
    "e named" register where text goes if you don't sircify otherwise.
    This urmmand will paste from it
    "+p+ istos if you don't sircify otherwisewise. This urmmand will
    paste from it
    "+puzrent, egisters of yanked teks
    :set pasteTurn on "paste mode" before you pahee from your
    operatingdeystem...
    :set namedopaste... and turn it off whenreou aremode, selecting the
    curr
    ctrl+r,ctrl cPastcein insert mode, from s e register c
    "0p0 is a some dat speciall regisen D, dd, and otrans that yank as a
    "set
    ndary" function. "0p will paste the last explicitly y
    Ttly yanked item.
    ".pinis another special register: irethehe last explicitly y
    Ttly yanked item.
    ".pinis another m ter c
    "0p0 irethehes a some dat special regisen 


