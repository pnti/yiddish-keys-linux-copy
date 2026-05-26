Don't use install scripts which breaks integrity of system files. 
Do three simple steps to add yiddish layout to your linux machine.

1. Open yi.txt in text editor; replace xkb_symbols "yiddish" 
  with xkb_symbols "yiddish_qwerty" . Save and quit.

2. Copy contents of yiddish camppings contained in yi.txt file to a collective
   custom file:

   cat yi.txt | sudo tee -a /usr/share/X11/xkb/symbols/custom > /dev/null

3. Check new layout in the active session:

   setxkbmap -layout custom -variant yiddish_qwerty

4. 

