Don't use install script which breaks the integrity of system files and crashes upgrade scipts. 
Use dedicated, official mechanism XKB Custom Layouts instead.

Follow these simple steps to add a Yiddish layout to your Linux machine.

1. Open yi.txt in text editor; replace xkb_symbols "yiddish" 
  with xkb_symbols "yiddish_qwerty" . Save and quit.

2. Copy the contents of the Yiddish mappings contained in the yi.txt file to a collective custom file:

   `cat yi.txt | sudo tee -a /usr/share/X11/xkb/symbols/custom > /dev/null`

3. Check new layout in the active session:

   `setxkbmap -layout custom -variant yiddish_qwerty`

4. To see this new layout in System Settings you have to register it.

5. Open evdev.xml in a text editor. Try to locate existing yi section.

   `grep -n '<name>yi</name>' /usr/share/X11/xkb/rules/evdev.xml`

6. If found add new layout to it. Find <variantList></variantList> and add definition of your layout.

   ```html
   <variant>
    <configItem>
      <name>custom+yiddish_qwerty</name>
      <shortDescription>yi-qw</shortDescription>
      <description>Yiddish (Daniel Nemenyi)</description>
    </configItem>
   </variant>

7. If not found add your variant definition to the existing custom layout in the same file. Locate *custom* layout. Inside evdev.xml search for <name>custom</name> inside evdev.xml .
   
8. Then locate probably empty `<variantList/>` tag. Replace it with a pair of `<variantList>` and `</variantList>` tags, and add your definition inside:

   ```html
   <variant>
      <configItem>
        <name>yiddish_qwerty</name>
        <shortDescription>yi</shortDescription>
        <description>Yiddish (QWERTY - Daniel Nemenyi)</description>
        <languageList>
          <iso639Id>yid</iso639Id>
        </languageList>
      </configItem>
    </variant>

9. Reboot.

10. Add the new layout selecting *Yiddish* language from *System Settings > Keyboard > Layout ... Add* .

11. Enjoy.
