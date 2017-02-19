# Script Player

## It allows you to manipulate the properties of windows and controls at run time.
Just add global extension "ScriptPlayer", and run the program with a command line parameter: "Myapp.exe ScriptPlayer=Myscript.xml"  
**You don't need to write any line of code!**

[Short video](https://youtu.be/u4rh6TUYwd4)

## History

### v1.04
- Bugfixes, improvements and new features.  
See [release notes](https://github.com/mikeduglas/Script-Player/releases/tag/v1.04) for details.

### v1.03
- Localization has has never been easier! New attribute "language" (global or procedure level) defines "language" section where all texts are located.
- Pseudo-event "BeforeAcceptLoop" allows to set SYSTEM properties before ACCEPT loop (this is necessary for example to localize main frame menu: SYSTEM{PROP:CharSet}=CHARSET:CYRILLIC).
- PROPLIST:xxx allowed.
- PROPSTYLE:xxx allowed.
- For properties which expect COLOR value, now you can use "color" attribute.
- Properties which are arrays now can use "index" attribute.
  
See [release notes](https://github.com/mikeduglas/Script-Player/releases/tag/v1.03) for details.

### v1.02
- you can now set properties for "System" variable.
- events "AlertKey" and "PreAlertKey" can be limited by key pressed.
- new action "Export" allows to export LIST contents to Excel2007/Html/Xml/Csv formats.
- you can now specify "logfile" (on global or procedure level), to automatically log the program behaviour (procedure name, thread, event, field, keycode).  
Events placed in log file are: EVENT:Accepted, EVENT:AlertKey, EVENT:CloseDown, EVENT:CloseWindow, EVENT:NewSelection, EVENT:OpenWindow.
  
See [release notes](https://github.com/mikeduglas/Script-Player/releases/tag/v1.02) for details.

### v1.01
- new ACTION:ChangeText - shortcut for SetProp(text) and allows to significally reduce amount of script lines.  
- new "type" attribute for actions used to set properties of all controls with same type at once. See available types in docs\types.txt.
- new <global> section applied to all procedures in an app.
- template now generates app-CONTROLS.txt file with type of controls.
  
See [release notes](https://github.com/mikeduglas/Script-Player/releases/tag/v1.02) for details.

### v1.00  
Initial release


## Demo appliaction
Standard School app with ScriptPlayer template. If you run school.exe without command line parameter, the program behavior is not changed.
If you run "school.exe ScriptPlayer=school.xml" (or provided school_test.cmd), you'll see the difference:
- All main menu items are "translated" (just UPPERCASEd for simplicity)
- All buttons are flat
- Main frame title text is changed
- Procedure BrowseStudents is called
- In BrowseStudents:   
active TAB is changed to 2nd  
"Close" button is **bold**  
listbox is colorized  
Export to Excel|Html|Xml|CSV allowed
- On exit of application the MESSAGE("Bye-bye") is thrown.
- school.log file created.

## XML script
In scripts you can use almost all events and writeable window/control properties. It allowed to POST(Event:Accepted), POST(Event:Selected), set window/control properties, or evaluate expressions.
Full list of available events, actions, and properties see in the \docs subfolder.


- See "docs\How-To.txt" to learn more about script syntax.
- Also see provided school.xml script, it contains the comments.


## Requirements
- C6 and higher, ABC/Legacy
- [EasyXML](http://www.ingasoftplus.com/ProductDetail.php?ProductID=293)


No black boxes, only pure Clarion code (class and template).

## Price
$35

## Contacts
[mikeduglas@yandex.ru](mailto: mikeduglas@yandex.ru)  
[mikeduglas66@gmail.com](mailto: mikeduglas66@gmail.com)
