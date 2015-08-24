---
layout: post
title: Vim Quick Start Guide
date: 2015-06-17 18:49:02.000000000 +05:30
---


##### Modes
* Insert Mode  <code> i </code>
* Leave Insert <code>Esc</code>
* Save file    <code>:write nameoffiel.txt</code>
* Quit         <code>:q</code>


##### Faster movements

move from word to word  <code>w & W </code>
Move back word to word  <code> b & B</code>

End of Line <code> $ </code>
Beginning of Line <code> ^ || 0 </code>

Beginning of file <code> gg </code>
End of file <code> Shift + G </code>

For paragraph to paragraph { , } 

Find in the same line <code> f + wordletter # (eg:: fw - goes to word beginnign with w letter ) 2fw , 3fw </code>

Line navigation <code> j, k  </code>

eg     <code> 3j # goes 3 lines down  </code>
       </code> 3k goes 3 lines up </code>


##### Basic editing

* Deleting letter - x
* Undo - u
* delete word - dw
* delet word and insert - cw
* delete entire line with line itself - dd
* delete entire line and write - cc ( Remember c to change)

<blockquote> "Hello there! whats up" - Remove text but not string using - ct" , ci"</blockquote>

in above syntax to remove quotes itself use ca" (remember a for around)


###### Copy/ Pasting 
Cut the text same as deleting - dw, or dd 
Paste the text - p (after cursor ) , P (before cursor)
Copy - y is for copying ( yw, yy ...) (y0 to copy everything behind cursor to start of line )


##### Search 

/nameofsearch  (forward search)
?nameofsearch (Backward search)
to search forward many occurences - n
Search backward - N

To select while searching /vf + name of text  will search and selects 

###### To search automatically
<code>:set incsearch</code> (incremental search)

<code>:set ignorecase</code> (not casesensitive)

###### Highlight search
<code>:set h1search</code> 
<code>:noh1search </code> (disable ) or :noh

###### Search using regex
<code>/.[aeiou]</code>
<code>seach all</code> blank lines 
/\n\n

###### To delete from cursor to the search term
<code>d + /searchname</code>

###### To change from cursor to search term
 <code>c + /searchname</code>


##### To replace
* :s for substitude 
* :s/ where / is separator
* :s/vim/vi (to replace vim with vi)  (this is limited to the line we are on to)

###### to replace all then
:%s/vim/vi (all vim changes to vi entire file)
but if the above command had small observation to make and is 
eg ;:: vim is my favourite editor, thanks vim
 if i use above command in this line it'll replace first substitute in every line,
to come around above problem :%s/vim/vi/g  (where s is called substitute, g is global)

##### Visual Mode:: (v)

##### Visual Line Mode :: (Shift + V)

lets suppose , 
function {
....
.....
}
if you want to select all data inside function , place cursor at { and type v to visual mode and press %  to select all text until }
now if we press : then different notation will come then we can do anything here

as i replace text i'll use :<','>s/sdkfl/sid/gc 
where c is confirm flag


gv to select previous block





