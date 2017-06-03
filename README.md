# Script Player

## It allows you to manipulate the properties of windows and controls at run time.
Just add global extension "ScriptPlayer", and run the program with a command line parameter: "Myapp.exe ScriptPlayer=Myscript.xml" or set script name in INI file:
```
[ScriptPlayer]
Name=Myscript.xml
```
**You don't need to write any line of code!**

[Short video](https://youtu.be/CrBI9xyOm_c)

Areas of use:
- Easy localization
- Adapting to different screen resolutions
- Uniform GUI
- Quick "on field" redesign without the need to rebuild the app

Additional features:
- Export listboxes to Excel/HTML/CSV/XML
- Capture any window contents
- Call MESSAGE()
- Custom window caption
- Toggle FullScreen mode

## History

### v2.03
- NEW: FullScreen mode. You can define hot key to toggle the application between FullScreen and Windowed modes:
```xml
    <procedure name="Main" fullscreenkey="F12"/>
```
School.exe supports F12 key to toggle FullScreen mode.

- CHG: APPNAME-CONTROLS.txt file now contains LIST and COMBO fields and field properties:  
```
      LIST         ?Browse:1
          Field #01    TEA:LastName 
            Header       Last Name
            Picture      @S20
            Format       80L(2)|M~Last Name~@S20@
          Field #02    TEA:FirstName 
            Header       First Name
            Picture      @S20
            Format       80L(2)|M~First Name~@S20@
          Field #03    MAJ:Description 
            Header       Department
            Picture      @S20
            Format       80L(2)|M~Department~@S20@
```
### v2.02
- FIX: command line corruption.
- FIX: Window{PROP:Pixels} was not restored.
- CHG: new procedure's attributes "starts-with" and "contains".
- CHG: height of custom caption can be specified.
- CHG: themed controls now can accept "disabled" values.

See [release notes](https://github.com/mikeduglas/Script-Player/releases/tag/v2.02) for details.

### v2.01
- FIX: possible program crash on window closing if custom caption used.
- NEW: "inactivetext" caption's section allows to define caption text properties when a window gets inactive.

See [release notes](https://github.com/mikeduglas/Script-Player/releases/tag/v2.01) for details.

### v2.00
- NEW: window themes. A theme is a combination of window/controls visual properties, like background, color, font style etc. 
- NEW: custom window caption.
- NEW: window animations (at this moment enabled only when closing windows).

See [release notes](https://github.com/mikeduglas/Script-Player/releases/tag/v2.00) for details.

### v1.10
- NEW: inline function parameters.
- CHG: school.xml now includes the code to prevent program hanging caused by App frame menu activation.

See [release notes](https://github.com/mikeduglas/Script-Player/releases/tag/v1.10) for details.

### v1.09
- Property conditions added. For example, you can change pictures to @d10-b for all entries whose picture is @d1.

See [release notes](https://github.com/mikeduglas/Script-Player/releases/tag/v1.09) for details.

### v1.08
- Support for field="?" added (it assumes current field returning by FIELD() function)

See [release notes](https://github.com/mikeduglas/Script-Player/releases/tag/v1.08) for details.

### v1.07
- "Export" now supports Page loaded browse boxes.

### v1.06
- new action "CALL" allows to call Clarion functions (over 20 functions: Logic Control, Event/Window/Keyboard/Drag-and-Drop Processing, Operating System Procedures);
- discount period expired.  

See [release notes](https://github.com/mikeduglas/Script-Player/releases/tag/v1.06) for details.

### v1.05
- new ACTION:Capture to capture active window;
- new "charset" attribute of properties (applied to "charset", "fontcharset" and "style:charset" properties).  
See [release notes](https://github.com/mikeduglas/Script-Player/releases/tag/v1.05) for details.

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
- Pressing Ctrl-Shift-P captures active window and saves the image on disk.

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
v1.xx - $80
v2.xx - $120

## Contacts
[mikeduglas@yandex.ru](mailto: mikeduglas@yandex.ru)  
[mikeduglas66@gmail.com](mailto: mikeduglas66@gmail.com)
