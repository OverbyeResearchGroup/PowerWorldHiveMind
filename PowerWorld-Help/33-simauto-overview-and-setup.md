---
title: "SimAuto — Overview and Setup"
part: "Scripting & Automation"
chapter_file: "33-simauto-overview-and-setup.md"
topics: 16
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# SimAuto — Overview and Setup

Starting SimAuto, accessing data, properties and object variables.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (16)**

- [Automation Server](#automation-server)
- [Installing Simulator Automation Server](#installing-simulator-automation-server)
- [Including Simulator Automation Server Functions](#including-simulator-automation-server-functions)
- [Connecting to Simulator Automation Server](#connecting-to-simulator-automation-server)
- [Passing Data to the Simulator Automation Server](#passing-data-to-the-simulator-automation-server)
- [Getting Data from the Simulator Automation Server](#getting-data-from-the-simulator-automation-server)
- [ExcelApp](#excelapp)
- [ExcelApp Sample Code](#excelapp-sample-code)
- [CreateIfNotFound](#createifnotfound)
- [CurrentDir](#currentdir)
- [CurrentDir Sample Code](#currentdir-sample-code)
- [ProcessID](#processid)
- [ProcessID Sample Code](#processid-sample-code)
- [ProgramInformation](#programinformation)
- [RequestBuildDate](#requestbuilddate)
- [UIVisible](#uivisible)

---

<a id="automation-server"></a>

## Automation Server

*Source: [`Content/MainDocumentation_HTML/Simulator_Automation_Server.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Simulator_Automation_Server.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

**The SimAuto tool is only available if you have purchased the SimAuto add-on to the base Simulator package. [Contact PowerWorld Corporation](52-additional-linked-topics-part1.md#contact-information)** **for details about ordering the SimAuto version of Simulator.**

SimAuto provides PowerWorld customers the ability to access PowerWorld Simulator functionality within a program written externally by the user. The Simulator Automation Server acts as a COM object, which can be accessed from various programming languages that have COM compatibility. Examples of programming tools with COM compatibility are Borlandâ Delphi, Microsoftâ Visual C++, Microsoftâ Visual Basic, and Matlabâ (among others). For more information on COM Objects and Automation Servers, see the help for Microsoft Windows.

The Automation Server of Simulator works very well in combination with Simulator Script Commands and [Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux). It is beneficial to become familiar with these topics when considering using the Simulator Automation Server.

Previous users of SimAuto in Version 9 will need to update their function calls to SimAuto functions. PowerWorld Corporation found it imperative to change the function calls for SimAuto, in order to remedy irreconcilable problems when using SimAuto with some programming languages. The documentation provided should provide adequate help on the changes needed, but as always, if any questions arise, please [contact](52-additional-linked-topics-part1.md#contact-information) PowerWorld Corporation for more information.

Note: When Simulator is launched using the SimAuto object, any currently running instances of Simulator launched manually will be unaffected. SimAuto will launch a separate background instance of Simulator so that any manually opened instances of Simulator can continue to be used by the user.

---

<a id="installing-simulator-automation-server"></a>

## Installing Simulator Automation Server

*Source: [`Content/MainDocumentation_HTML/Installing_Simulator_Automation_Server.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Installing_Simulator_Automation_Server.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Note that previous users of SimAuto in Version 9 will need to update their function calls to SimAuto functions. PowerWorld Corporation found it imperative to change the function calls for SimAuto, in order to remedy irreconcilable problems when using SimAuto with some programming languages. The documentation provided should provide adequate help on the changes needed, but as always, if any questions arise, please contact PowerWorld Corporation for more information.

Installing the [Simulator Automation Server](#automation-server) requires no additional steps beyond installing PowerWorld Simulator as normal. When a version of PowerWorld Simulator containing the Simulator Automation Server is installed on your computer, the install program automatically adds the information needed by the Simulator Automation Server to the registry.

If for some reason the registration fails, be sure you have the SimAuto add-on for Simulator. You can fix registration issues by using the Register SimAuto tool that is installed with Simulator.

---

<a id="including-simulator-automation-server-functions"></a>

## Including Simulator Automation Server Functions

*Source: [`Content/MainDocumentation_HTML/Including_Simulator_Automation_Server_Functions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Including_Simulator_Automation_Server_Functions.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Before you can access the functions defined by the [Simulator Automation Server](#automation-server) when writing the code for your external program, you must first include the library of functions defined for the Simulator Automation Server. This kind of library is referred to as a Type Library, which describes the available functions in a manner that can be interpreted by different programming languages. Importing a Type Library from another program is usually fairly simple, but the procedure does vary depending on the programming tool you are using. Please see the help for your programming tool of choice on how to import a Type Library or COM functions from another program.

Examples

The following examples are just a few specific examples for certain programming media. The procedure may be different for other programming media not listed. In addition, a procedure given for a certain type of programming media may be one variation from several possible procedures for accomplishing the same task.

Borland Delphi

  - Install the version of PowerWorld Simulator with the Simulator Automation Server included.
  - In Delphi, choose **Import Type Library**… from the Project menu.
  - In the list of libraries, search for and choose pwrworld Library.
  - If pwrworld Library is not in the list, click **Add**. Find and choose the Pwrworld.exe file from the PowerWorld Simulator directory, and click **Open**.
  - You should see the class name TSimulatorAuto in the list of Class names.
  - Click **Install** to include the PowerWorld Simulator Type Library.

Microsoft Visual Basic for Applications

  - No additional tasks are necessary
  - Importing Type Library still works (See [Including Functions for version 9](52-additional-linked-topics-part1.md#including-simulator-automation-server-functions-version-9)).

Microsoft Visual C++

  - Install the version of PowerWorld Simulator with the Simulation Automation Server included.
  - Add **\#import "…\\powerworld.exe"** in your external program code, using the full path to the PowerWorld Simulator executable program.
  - Add **using namespace pwrworld** in your external program code.

Matlab v.6.5 r.13

  - No additional tasks are necessary.

---

<a id="connecting-to-simulator-automation-server"></a>

## Connecting to Simulator Automation Server

*Source: [`Content/MainDocumentation_HTML/Connecting_to_Simulator_Automation_Server.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Connecting_to_Simulator_Automation_Server.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Once the Type Library or COM functions have been included in your programming environment, the [Simulator Automation Server](#automation-server) can be handled as any other object in your code. The method for assigning and connecting to the Simulator Automation Server can vary depending on the programming environment used, but the idea is basically the same. You define a variable in your program to point to the server object, which is called SimulatorAuto. If the Type Library was imported properly, you should have full access to the SimulatorAuto object and its defined functions. Again, the procedure for creating the object and connecting to SimulatorAuto may vary for different programming languages. Check the help for your programming environment on connecting to COM or Automation servers.

Examples

The following examples are just a few specific examples for certain programming media. The procedure may be different for other programming media not listed. In addition, a procedure given for a certain type of programming media may be one variation from several possible procedures for accomplishing the same task.

Borland Delphi 5

  - Add **pwrworld\_TLB** to the **uses** section of your unit.
  - Declare a variable globally or as part of another object: **A : ISimulatorAuto**
  - Initialize the variable: **A := nil**
  - To connect to the Simulator Automation Server, create the connection: **A := CoSimulatorAuto.create**
  - Perform function calls to the Simulator Automation Server: **Output :=** **A.SomeFunction(parameters)**
  - To close the connection to the Simulator Automation Server, remove the reference by again setting: **A := nil**

Microsoft Visual Basic for Applications

Early Binding:

  - To connect to the Simulator Automation Server, create the connection initializing the variable:

**Dim A as New pwrworld.SimulatorAuto**

Late Binding:

  - Declare a variable globally or as part of another object or function: **Dim A As Object**
  - To connect to the Simulator Automation Server, create the connection:

**Set A = CreateObject("pwrworld.SimulatorAuto")**

Both Early and Late Binding:

  - Perform function calls to the Simulator Automation Server: **Output =** **A.SomeFunction parameters**
  - To close the connection to the Simulator Automation Server, remove the reference: **Set A = Nothing**
  - If Type Library was imported, connection can also be achieved as in version 9 (See [Connecting to Simulator Automation Server in version 9](#)).

Microsoft .NET

  - Connect to the Simulator Automation Server in one of the manners given above
  - Perform function calls as given above
  - The .NET environment does not release all resources immediately, but when the opportunity arises. Using the method described above, i.e. **Set A = Nothing**, may not release the Simulator Automation Server instance. To force the Simulator Automation Server to close, use the following code snippet:

Marshal.FinalReleaseComObject(A)

Set A = Nothing

  - To learn more about this function, go to the Microsoft MSDN documentation at: <http://msdn.microsoft.com/en-us/library/system.runtime.interopservices.marshal.finalreleasecomobject.aspx>

Microsoft Visual C++

  - Declare a variable globally or as part of another object or function: **IsimulatorAutoPtr \*A**
  - Declare a variable globally or as part of another object or function: **CLSID clsid**
  - Declare a variable globally or as part of another object or function: **HRESULT hr**
  - Obtain the class identifier (clsid) with the following command:

**hr = CLSIDFromProgID(L"pwrworld.SimulatorAuto", \&clsid)**

  - Initialize variable A: **A = new IsimulatorAutoPtr**
  - To connect to the Simulator Automation Server, create the connection:

**hr = A\>CreateInstance(clsid, NULL, CLSCTX\_SERVER)**

  - Perform function calls to the Simulator Automation Server: **Output =** **A.SomeFunction(parameters)**
  - To close the connection to the Simulator Automation Server, release the reference:

**hr = A\>Release()**

Python

  - COM connections require pyWin32 extensions
  - The following will establish a connection:

import win32com.client

object = win32com.client.Dispatch("pwrworld.SimulatorAuto")

  - The following will close the connection:

del object

object = None

Matlab v.6.5 r.13

  - To connect to the Simulator Automation Server, create the connection:

**A = actxserver(‘pwrworld.SimulatorAuto’)**

  - Perform function calls to the Simulator Automation Server: **Output =** **A.SomeFunction(parameters)**
  - To close the connection to the Simulator Automation Server, delete the connection: **delete(A)**

---

<a id="passing-data-to-the-simulator-automation-server"></a>

## Passing Data to the Simulator Automation Server

*Source: [`Content/MainDocumentation_HTML/Passing_Data_to_the_Simulator_Automation_Server.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Passing_Data_to_the_Simulator_Automation_Server.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Passing Data to the Simulator Automation Server

Most data to the Simulator Automation Server is passed by value rather than by reference (in pointer terminology, this corresponds to sending data instead of pointer to data; in Microsoft Visual Basic®, this corresponds to sending data ByVal instead of ByRef). The individual function descriptions will indicate if results are returned through passed parameters.

No Optional Parameters

There are no optional parameters for any of the Simulator Automation functions. All functions must be called with every argument filled.

---

<a id="getting-data-from-the-simulator-automation-server"></a>

## Getting Data from the Simulator Automation Server

*Source: [`Content/MainDocumentation_HTML/Getting_Data_from_the_Simulator_Automation_Server.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Getting_Data_from_the_Simulator_Automation_Server.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Output Structure

Most functions called on the SimulatorAuto object returns the same value, Output, which has a well-defined structure.

Output is of type **VARIANT**, and is an array of **VARIANT**s. Output is zero-indexed.

The first element *always* contains any errors occurring during execution. For those functions returning more than one element in the Output array (e.g. ListOfDevices), explanation is provided below when discussing the specific method.

Individual function descriptions will indicate the format and data type of the returned parameters.

Error Handling

When the output format is a variant array of variants as mentioned above, the first item in the Output VARIANT array, Output\[0\], contains any errors occurring during the function’s execution. If no errors occurred during the function’s execution, Output\[0\] will be set to an empty BSTR (string) represented in most languages by either ‘’ or "".

Error Format

If an error string is returned when the output format is a variant array of variants, it will be in the following format:

\[method name\]: \[error\_explanation\]

e.g. RunScriptCommand: Error occurred processing script command – check command syntax

---

<a id="excelapp"></a>

## ExcelApp

*Source: [`Content/MainDocumentation_HTML/ExcelApp_Property.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ExcelApp_Property.htm)*

The [Simulator Automation Server](#automation-server) has the ability to send data from Simulator to an Excel spreadsheet using the [SendToExcel](34-simauto-functions.md#sendtoexcel). By default, the Simulator Automation Server starts an instance of Excel the first time one of the above functions is called. Each subsequent call to these two functions will then send data to the same instance of Excel, until it is manually closed by the user. The ExcelApp property allows the user to gain access to the instance of Excel used by the Simulator Automation Server from within its own code. Thus the user can write code to manipulate the external instance of Excel. In addition, the ExcelApp property can be set by the user’s code, meaning that the user can initialize an external instance of Excel from within their own code and set the ExcelApp property to their external instance of Excel. Simulator itself is limited to starting only one instance of Excel on its own, but with the ExcelApp property allowing you to set the instance of Excel that Simulator uses on the fly, you can generate multiple instances of Excel within your code, and handle setting the ExcelApp property of the Simulator Automation server to the desired Excel instance depending on the data you want to send to Excel.

The ExcelApp property is a variable of type Variant that returns the pointer to an object representing the external instance of Excel.

**ExcelApp : Variant**

To gain access to the external instance of Excel stored in the ExcelApp property, you first need to initialize a variable as an object. The following are a couple of examples in Borland Delphi and Microsoft Visual Basic.

Examples

Borland Delphi 5

  - **Var MyExc : TObject**
  - **MyExc = SimAuto.ExcelApp***{Makes the connection to the external instance}*
  - *{Perform activities with the Excel instance}*
  - **MyExc.Quit***{Closes the external instance if called; do not call if you wish the instance to remain open}*
  - **MyExc.Free***{Removes the connection to the external instance}*

Microsoft Visual Basic

  - **Dim MyExc As Variant**
  - **Set MyExc = SimAuto.ExcelApp***{Makes the connection to the external instance}*
  - *{Perform activities with the Excel instance}*
  - **MyExc.Quit***{Closes the external instance if called; do not call if you wish the instance to remain open}*
  - **Set MyExc = Nothing***{Removes the connection to the external instance}*

---

<a id="excelapp-sample-code"></a>

## ExcelApp Sample Code

*Source: [`Content/MainDocumentation_HTML/ExcelApp_Sample_Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ExcelApp_Sample_Code.htm)*

Microsoft® Visual Basic for Applications

Dim ExcelObject As Variant

If Not (IsEmpty(SimAuto.ExcelApp)) Then

Set ExcelObject = SimAuto.ExcelApp 

ExcelObject.DisplayAlerts = False 

ExcelObject.Quit 

Else

MsgBox("Attempted to obtain Excel COM object from " + \_ 

"Simulator, but there is not one open.") 

End If

Matlab®

*MATLAB is currently unable to handle COM object properties returning COM objects themselves, such as the ExcelApp property of Simulator.*

---

<a id="createifnotfound"></a>

## CreateIfNotFound

*Source: [`Content/MainDocumentation_HTML/CreateIfNotFound_Property.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/CreateIfNotFound_Property.htm)*

The CreateIfNotFound property of the [Simulator Automation Server](#automation-server) is useful when you are changing data with the ChangeParameters functions ([ChangeParameters](52-additional-linked-topics-part1.md#changeparameters-function), [ChangeParametersSingleElement](34-simauto-functions.md#changeparameterssingleelement), [ChangeParametersMultipleElement](34-simauto-functions.md#changeparametersmultipleelement), and [ChangeParametersMultipleElementFlatInput](34-simauto-functions.md#changeparametersmultipleelementflatinput)). Set CreateIfNotFound = *True* if objects that are updated through the ChangeParameters functions should be created if they do not already exist in the case. Objects that already exist will be updated. Set CreateIfNotFound = *False* to not create new objects and only update existing ones. The CreateIfNotFound property is global, once it is set to *True* this applies to all future ChangeParameters calls.

---

<a id="currentdir"></a>

## CurrentDir

*Source: [`Content/MainDocumentation_HTML/CurrentDir_Property.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/CurrentDir_Property.htm)*

The CurrentDir property of the [Simulator Automation Server](#automation-server) allows you to retrieve or set the working directory for the currently running SimulatorAuto process. This is most useful if using relative filenames (e.g. "relativename.aux" versus "C:\\Program Files\\PowerWorld\\Working\\abosultename.aux") when specifying files.

---

<a id="currentdir-sample-code"></a>

## CurrentDir Sample Code

*Source: [`Content/MainDocumentation_HTML/CurrentDir_Sample_Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/CurrentDir_Sample_Code.htm)*

Microsoft® Visual Basic for Applications

' Display the current directory

MsgBox(SimAuto.CurrentDir)

' Set the current directory to c:\\

SimAuto.CurrentDir = "c:\\"

Matlab®

% Display the current directory

disp(SimAuto.CurrentDir)

% Set the current directory to c:\\

SimAuto.CurrentDir = 'c:\\';

---

<a id="processid"></a>

## ProcessID

*Source: [`Content/MainDocumentation_HTML/ProcessID_Property.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ProcessID_Property.htm)*

The ProcessID property of the [Simulator Automation Server](#automation-server) allows you to retrieve the process ID of the currently running SimulatorAuto process, as can also be seen through the Task Manager in Windows®. This information can be useful if a forced shutdown of the SimulatorAuto object is needed, as all calls to the SimulatorAuto object are synchronous. This means the SimulatorAuto object will not be destroyed until all calls, no matter the time of execution, have completed.

---

<a id="processid-sample-code"></a>

## ProcessID Sample Code

*Source: [`Content/MainDocumentation_HTML/ProcessID_Sample_Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ProcessID_Sample_Code.htm)*

Microsoft® Visual Basic for Applications

' Display the process ID

MsgBox(SimAuto.ProcessID)

Matlab®

% Display the process ID

disp(num2str(SimAuto.ProcessID))

---

<a id="programinformation"></a>

## ProgramInformation

*Source: [`Content/MainDocumentation_HTML/ProgramInformation_Property.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ProgramInformation_Property.htm)*

Added in version 21, build on August 4, 2020)

This property is available starting with the *pwrworld 21.0 type library*.

The ProgramInformation property of the [Simulator Automation Server](#automation-server) returns information about the version of PowerWorld Simulator run by the current instance of SimAuto.

Output

This property returns a variant array of variant arrays. The order of each array within the main array is subject to change and additional arrays may be added in the future. The first entry of each array will indicate what type of information is in the array. The order of entries within each array will not change. The identifying first entry for each array is as follows:

**version** - contains the version number, patch date, and version string

**addons** - contains the list of available add-ons ordered by add-on followed by their expiration dates

**executable** - contains the path of the PowerWorld Simulator executable in use

---

<a id="requestbuilddate"></a>

## RequestBuildDate

*Source: [`Content/MainDocumentation_HTML/RequestBuildDate_Property.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/RequestBuildDate_Property.htm)*

The RequestBuildDate property of the [Simulator Automation Server](#automation-server) allows you to retrieve the build date of the PowerWorld Simulator executable currently running with the SimulatorAuto process. The property returns an integer value that represents a date. This information is useful for verifying the release version of the executable.

---

<a id="uivisible"></a>

## UIVisible

*Source: [`Content/MainDocumentation_HTML/UIVisible_Property.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/UIVisible_Property.htm)*

The UIVisible property of the [Simulator Automation Server](#automation-server) allows you to toggle the visibility of the user interface for Simulator. Default behavior is to not show the user interface while using SimAuto. Set this property to *True* to show the user interface and *False* to hide the user interface.

This property is available starting with the *pwrworld 20.0 type library*.
