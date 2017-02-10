# Script Player

## It allows you to manipulate the properties of windows and controls at run time.
Just add global extension "ScriptPlayer", and run the program with a command line parameter: "Myapp.exe ScriptPlayer=Myscript.xml"

## Demo appliaction.
Standard School app with ScriptPlayer template. If you run school.exe without command line parameter, the program behavior is not changed.
If you run "school.exe ScriptPlayer=school.xml" (or provided school_test.cmd), you'll see the difference:
- All main menu items are "translated" (just UPPERCASEd for simplicity)
- Main frame title text is changed
- Procedure BrowseStudents is called
- In BrowseStudents active TAB is changed to 2nd
- In BrowseStudents "Close" button is **bold**
- On exit of application the MESSAGE("Bye-bye") is thrown.

## XML script.
See provided school.xml script, it contains the comments.
In scripts you can use almost all events and writeable window/control properties. It allowed to POST(Event:Accepted), POST(Event:Selected), set window/control properties, or evaluate an expressions.
Full list of available events, actions, and properties see in the docs.

##Requirements
[EasyXML](http://www.ingasoftplus.com/ProductDetail.php?ProductID=293)

