# Script Player

## It allows you to manipulate the properties of windows and controls at run time.
Just add global extension "ScriptPlayer", and run the program with a command line parameter: "Myapp.exe ScriptPlayer=Myscript.xml"


## History

### v1.01
- new ACTION:ChangeText - shortcut for SetProp(text) and allows to significally reduce amount of script lines. For example,
```xml
      <!-- Using ACTION:SetProp and PROP:Text -->
      <action name="SetProp" field="?MENU1">
        <property name="text" value="&amp;FILE"></property>
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
- On exit of application the MESSAGE("Bye-bye") is thrown.

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
$25

## Contacts
[mikeduglas@yandex.ru](mailto: mikeduglas@yandex.ru)  
[mikeduglas66@gmail.com](mailto: mikeduglas66@gmail.com)
