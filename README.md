# Script Player

## It allows you to manipulate the properties of windows and controls at run time.
Just add global extension "ScriptPlayer", and run the program with a command line parameter: "Myapp.exe ScriptPlayer=Myscript.xml"  
**You don't need to write any line of code!**


## History

### v1.03
- Localization has has never been easier! New attribute "language" (global or procedure level) defines "language" section where all texts are located:  
```xml
<?xml version="1.0" encoding="windows-1251"?>
<script>
  <global language="Russian"/>
  <!-- <procedure language="Russian"/> -->

  <language name="Russian">
    <!-- File menu -->
    <procedure name="Main">
      <field name="?MENU1">Файл</field>
      <field name="?PrintSetup">Установка принтера ...</field>
      <field name="?Exit">Выход</field>
    </procedure>
  </language>
</script>
```  
  
- Pseudo-event "BeforeAcceptLoop" allows to set SYSTEM properties before ACCEPT loop (this is necessary for example to localize main frame menu: SYSTEM{PROP:CharSet}=CHARSET:CYRILLIC):
```xml
  <procedure name="Main">
    <event name="BeforeAcceptLoop">
      <action name="SetProp" field="System">
        <property name="CharSet" value="204"></property>
      </action>
    </event>
  </procedure>
```  
  
- PROPLIST:xxx allowed:  
```xml
    <property name="list:Underline" value="1"/>
```
- PROPSTYLE:xxx allowed:  
```xml
    <property name="style:fontname" value="Arial"/>
```
- For properties which expect COLOR value, now you can use "color" attribute:  
```xml
    <property name="list:DefHdrTextColor" color="White"/>
```
- Properties which are arrays now can use "index" attribute:  
```xml
    <property name="list:ColStyle" index="1" value="1"/>
```
  
### v1.02
- you can now set properties for "System" variable:
```xml
  <action name="SetProp" field="System">
    <property name="notips" value="1"></property>
  </action>
```  

- events "AlertKey" and "PreAlertKey" can be limited by key pressed.
- new action "Export" allows to export LIST contents to Excel2007/Html/Xml/Csv formats:
```xml
  <!-- Initialize window and controls -->
  <event name="OpenWindow">
    <!-- Assign hots key to ?Browse:1 -->
    <action name="SetProp" field="?Browse:1">
      <property name="Alrt" value="CtrlShiftE"></property>
      <property name="Alrt" value="CtrlShiftH"></property>
      <property name="Alrt" value="CtrlShiftS"></property>
    </action>
  </event>

  <!-- Export ?Browse:1 contents -->
  <event name="alertkey" field="?Browse:1" key="CtrlShiftE">
    <action name="Export" field="?Browse:1" expression="Excel"></action>
  </event>
  <event name="alertkey" field="?Browse:1" key="CtrlShiftH">
    <action name="Export" field="?Browse:1" expression="Html"></action>
  </event>
  <event name="alertkey" field="?Browse:1" key="CtrlShiftS">
    <action name="Export" field="?Browse:1"></action>
  </event>
``` 

- you can now specify "logfile" (on global or procedure level), to automatically log the program behaviour (procedure name, thread, event, field, keycode):
```xml
  <global logfile="school.log"/>
```  
Events placed in log file are: EVENT:Accepted, EVENT:AlertKey, EVENT:CloseDown, EVENT:CloseWindow, EVENT:NewSelection, EVENT:OpenWindow.


### v1.01
- new ACTION:ChangeText - shortcut for SetProp(text) and allows to significally reduce amount of script lines.  
For example, place following block into "Main" procedure, "OpenWindow" event (in this case System{prop:NoTips}=1 will be called only once):
```xml
      <!-- Globally disable tooltips -->
      <action name="SetProp" field="System">
        <property name="notips" value="1"></property>
      </action>
```  

```xml
      <!-- Using ACTION:ChangeText -->
      <action name="ChangeText" field="?MENU1" expression="&amp;FILE"/>  
```

- new "type" attribute for actions used to set properties of all controls with same type at once. See available types in docs\types.txt.

- new <global> section applied to all procedures in an app.
Following example sets lineheight to "16" for all lists in entire app:

```xml
  <!-- Applied to all procedures -->
  <global>
    <event name="OpenWindow" position="1">
      
      <!-- Set LineHeight to 16 for all listboxes -->
      <action name="SetProp" type="list">
        <property name="lineheight" value="16"></property>
      </action>
    </event>
  </global>
```  

- template now generates app-CONTROLS.txt file with type of controls:

>    Procedure SplashIt  
>      STRING       ?String2  
>      STRING       ?String3  


### v1.00  
Initial release


## Demo appliaction
Standard School app with ScriptPlayer template. If you run school.exe without command line parameter, the program behavior is not changed.
If you run "school.exe ScriptPlayer=school.xml" (or provided school_test.cmd), you'll see the difference:
- All main menu items are "translated" (just UPPERCASEd for simplicity)
- Main frame title text is changed
- Procedure BrowseStudents is called
- In BrowseStudents active TAB is changed to 2nd
- In BrowseStudents "Close" button is **bold**
- Export from BrowseStudents to Excel|Html|Xml|CSV
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
