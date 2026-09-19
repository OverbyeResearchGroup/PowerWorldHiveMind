---
title: "SimAuto — Function Reference"
part: "Scripting & Automation"
chapter_file: "34-simauto-functions.md"
topics: 55
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# SimAuto — Function Reference

Every SimAuto function, with signature, parameters and examples.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (55)**

- [ChangeParametersSingleElement](#changeparameterssingleelement)
- [ChangeParametersSingleElement Sample Code](#changeparameterssingleelement-sample-code)
- [ChangeParametersMultipleElement](#changeparametersmultipleelement)
- [ChangeParametersMultipleElement Sample Code](#changeparametersmultipleelement-sample-code)
- [ChangeParametersMultipleElement Sample Code for Python](#changeparametersmultipleelement-sample-code-for-python)
- [ChangeParametersMultipleElementFlatInput](#changeparametersmultipleelementflatinput)
- [ChangeParametersMultipleElementFlatInput Sample Code](#changeparametersmultipleelementflatinput-sample-code)
- [ChangeParametersMultipleElementRect](#changeparametersmultipleelementrect)
- [CloseCase](#closecase)
- [CloseCase Sample Code](#closecase-sample-code)
- [GetCaseHeader](#getcaseheader)
- [GetFieldList](#getfieldlist)
- [GetFieldList Sample Code](#getfieldlist-sample-code)
- [GetParametersSingleElement](#getparameterssingleelement)
- [GetParametersSingleElement Sample Code Delphi](#getparameterssingleelement-sample-code-delphi)
- [GetParametersSingleElement Sample Code Matlab](#getparameterssingleelement-sample-code-matlab)
- [GetParametersSingleElement Sample Code VB](#getparameterssingleelement-sample-code-vb)
- [GetParametersMultipleElement](#getparametersmultipleelement)
- [GetParametersMultipleElement Sample Code Delphi](#getparametersmultipleelement-sample-code-delphi)
- [GetParametersMultipleElement Sample Code Matlab](#getparametersmultipleelement-sample-code-matlab)
- [GetParametersMultipleElement Sample Code VB](#getparametersmultipleelement-sample-code-vb)
- [GetParametersMultipleElementFlatOutput](#getparametersmultipleelementflatoutput)
- [GetParametersMultipleElementRect](#getparametersmultipleelementrect)
- [GetParamsRectTyped](#getparamsrecttyped)
- [GetParamsRectTyped Sample Code Python](#getparamsrecttyped-sample-code-python)
- [GetParamsTypedCols](#getparamstypedcols)
- [GetParamsTypedCols Sample Code Python](#getparamstypedcols-sample-code-python)
- [GetSpecificFieldList](#getspecificfieldlist)
- [GetSpecificFieldMaxNum](#getspecificfieldmaxnum)
- [ListOfDevices](#listofdevices)
- [ListOfDevices Sample Code Delphi](#listofdevices-sample-code-delphi)
- [ListOfDevices Sample Code Matlab](#listofdevices-sample-code-matlab)
- [ListOfDevices Sample Code VB](#listofdevices-sample-code-vb)
- [ListOfDevicesAsVariantStrings](#listofdevicesasvariantstrings)
- [ListOfDevicesFlatOutput](#listofdevicesflatoutput)
- [LoadState](#loadstate)
- [LoadState Sample Code](#loadstate-sample-code)
- [OpenCase](#opencase)
- [OpenCase Sample Code](#opencase-sample-code)
- [OpenCaseType](#opencasetype)
- [ProcessAuxFile](#processauxfile)
- [ProcessAuxFile Sample Code](#processauxfile-sample-code)
- [RunScriptCommand](#runscriptcommand)
- [RunScriptCommand Sample Code](#runscriptcommand-sample-code)
- [RunScriptCommand2](#runscriptcommand2)
- [SaveCase](#savecase)
- [SaveCase Sample Code](#savecase-sample-code)
- [SaveState](#savestate)
- [SaveState Sample Code](#savestate-sample-code)
- [SendToExcel](#sendtoexcel)
- [SendToExcel Sample Code](#sendtoexcel-sample-code)
- [TSGetContingencyResults](#tsgetcontingencyresults)
- [TSGetContingencyResults Sample Code](#tsgetcontingencyresults-sample-code)
- [WriteAuxFile](#writeauxfile)
- [WriteAuxFile Sample Code](#writeauxfile-sample-code)

---

<a id="changeparameterssingleelement"></a>

## ChangeParametersSingleElement

*Source: [`Content/MainDocumentation_HTML/ChangeParametersSingleElement_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ChangeParametersSingleElement_Function.htm)*

The ChangeParametersSingleElement function allows you to set a list of parameters for a single object in a case loaded into the [Simulator Automation Server](33-simauto-overview-and-setup.md#automation-server). In addition to changing parameters for objects, this function can also be used to set options for some of the Simulator tools, such as [ATC](32-available-transfer-capability.md#available-transfer-capability-atc-analysis) and [OPF](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview). This function is identical in setup to the [GetParametersSingleElement](#getparameterssingleelement) function, with the exception that the Values array must contain a value for each field variable given in the ParamList array.

Unlike the script SetData and CreateData commands, SimAuto does not have any explicit functions to create elements. Instead this can be done using the ChangeParameters functions by making use of the [CreateIfNotFound](33-simauto-overview-and-setup.md#createifnotfound) SimAuto property. Set CreateIfNotFound = True if objects that are updated through the ChangeParameters functions should be created if they do not already exist in the case. Objects that already exist will be updated. Set CreateIfNotFound = False to not create new objects and only update existing ones. The CreateIfNotFound property is global, once it is set to True this applies to all future ChangeParameters calls.

**Function Prototype**

**ChangeParametersSingleElement(ObjectType, ParamList, Values)**

Parameter Definitions

**ObjectType : String **The type of object for which parameters are being changed.

**ParamList : Variant **A variant array storing strings (COM Type BSTR). This array stores a list of PowerWorldâ object field variables, as defined in the section on [PowerWorld Object Fields](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names). The ParamList must contain the [key field](04-model-explorer-and-case-information-part3.md#key-fields) variables or [label](07-object-properties-run-mode-and-general-part2.md#labels) for the specific device, or the device cannot be identified.

**Values : Variant **A variant array storing variants. This array can store any type of information (integer, string, etc.) in each array position. A value should be passed for each field variable given in the ParamList. The Values array must contain the [key field](04-model-explorer-and-case-information-part3.md#key-fields) values for the specific device, or the device cannot be identified.

Output

ChangeParametersSingleElement only returns the first element in Output, the error string.

Notes

The ParameterList and Values arrays must be the same size, as each parameter must have a corresponding value to be assigned.

---

<a id="changeparameterssingleelement-sample-code"></a>

## ChangeParametersSingleElement Sample Code

*Source: [`Content/MainDocumentation_HTML/ChangeParametersSingleElement_Sample_Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ChangeParametersSingleElement_Sample_Code.htm)*

Borland® Delphi

Var ParamList, ValueList : OLEVariant

// Set ParamList up to modify the maximum number of iterations

// and the system base for the power flow simulations

ParamList := VarArrayCreate(\[1,2\], varOleStr);

ParamList\[1\] := 'MaxItr';

ParamList\[2\] := 'MVABase';

// ValueList is setup with 41 and 410 for MaxItr and MVABase,

// respectively

ValueList := VarArrayCreate(\[1,2\], varOleStr);

ValueList\[1\] := 41;

ValueList\[2\] := 410;

// Make the ChangeParametersSingleElement call

Output = SimAuto.ChangeParametersSingleElement('Sim\_Solution\_Options', \_

ParamList, ValueList) 

Microsoft® Visual Basic for Applications

' Set ParamList up to modify the maximum number of iterations

' and the system base for the power flow simulations

Dim ParamList As Variant

ParamList = Array("MaxItr", "MVABase")

' ValueList is setup with 41 and 410 for MaxItr and MVABase,

' respectively

Dim ValueList As Variant

ValueList = Array(41, 410)

' Make the ChangeParametersSingleElement call

Output = SimAuto.ChangeParametersSingleElement("Sim\_Solution\_Options", \_

ParamList, ValueList) 

Matlab®

% Set ParamList up to modify the maximum number of iterations

% and the system base for the power flow simulations

ParamList = {'MaxItr' 'MVABase'};

% values is setup with 41 and 410 for MaxItr and MVABase,

% respectively

values = \[41 410\];

% Convert the values matrix to a set of cells for passing

% through the COM interface

ValueList = num2cell(values);

' Make the ChangeParametersSingleElement call

Output = SimAuto.ChangeParametersSingleElement('Sim\_Solution\_Options', \_

ParamList, ValueList)

---

<a id="changeparametersmultipleelement"></a>

## ChangeParametersMultipleElement

*Source: [`Content/MainDocumentation_HTML/ChangeParametersMultipleElement_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ChangeParametersMultipleElement_Function.htm)*

The ChangeParametersMultipleElement function allows you to set parameters for multiple objects of the same type in a case loaded into the Simulator Automation Server. This function is very similar to the [ChangeParametersSingleElement](#changeparameterssingleelement), but allows for modifying multiple elements with a single function call. The advantage of this function is that it is much faster to change multiple elements with a single function call than it is to repeatedly call ChangeParametersSingleElement multiple times.

Unlike the script SetData and CreateData commands, SimAuto does not have any explicit functions to create elements. Instead this can be done using the ChangeParameters functions by making use of the [CreateIfNotFound](33-simauto-overview-and-setup.md#createifnotfound) SimAuto property. Set CreateIfNotFound = True if objects that are updated through the ChangeParameters functions should be created if they do not already exist in the case. Objects that already exist will be updated. Set CreateIfNotFound = False to not create new objects and only update existing ones. The CreateIfNotFound property is global, once it is set to True this applies to all future ChangeParameters calls.

**Function Prototype**

**ChangeParametersMultipleElement(ObjectType, ParamList, Values)**

Parameter Definitions

**ObjectType : String **The type of object for which parameters are being changed.

**ParamList : Variant **A variant array storing strings (COM Type BSTR). This array stores a list of PowerWorldâ object field variables, as defined in the section on [PowerWorld Object Fields](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names). The ParamList must contain the [key field](04-model-explorer-and-case-information-part3.md#key-fields) variables for the specific device, or the device cannot be identified.

**ValueList : Variant **A variant array storing arrays of variants. This is the difference between the multiple element and single element change parameter functions. This array stores a list of arrays of values matching the fields laid out in ParamList. You construct ValueList by creating an array of variants with the necessary parameters for each device, and then inserting each individual array of values into the ValueList array. SimAuto will pick out each array from ValueList, and calls ChangeParametersSingleElement internally for each array of values in ValueList.

Output

ChangeParametersMultipleElement only returns the first element in Output, the error string.

Notes

The ParameterList and each array of values stored in ValueList must be the same size, as each parameter must have a corresponding value to be assigned.

---

<a id="changeparametersmultipleelement-sample-code"></a>

## ChangeParametersMultipleElement Sample Code

*Source: [`Content/MainDocumentation_HTML/ChangeParametersMultipleElement_Sample_Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ChangeParametersMultipleElement_Sample_Code.htm)*

Borland® Delphi

Var ParamList, ValueList : OLEVariant

// Set ParamList up to modify the MW output of generators

ParamList := VarArrayCreate(\[1,3\], varOleStr);

ParamList\[1\] := 'BusNum';

ParamList\[2\] := 'ID';

ParamList\[3\] := ‘MW’;

// ValueList is setup with MW values for generators at buses 1 and 2

ValueList := VarArrayCreate(\[1,2\], varOleStr);

For k := 1 to 2 do begin

IndValueList := VarArrayCreate(\[1,3\], varOleStr);

IndValueList\[1\] := k;

IndValueList\[2\] := ‘1’;

IndValueList\[3\] := k\*10;

ValueList\[k\] := IndValueList;

End;

// Make the ChangeParametersMultipleElement call

Output = SimAuto.ChangeParametersMultipleElement('Gen', \_

ParamList, ValueList) 

Microsoft® Visual Basic for Applications

' Set ParamList up to modify the MW output of generators

Dim ParamList As Variant

ParamList = Array("BusNum", "ID", "MW")

' ValueList is setup with MW values for generators at buses 1 and 2

Dim ValueList(2) As Variant

For k = 0 to 1

Dim IndValueList As Variant

IndValueList = Array(k+1,"1",(k+1)\*10)

ValueList(k) = IndValueList

Next

' Make the ChangeParametersMultipleElement call

Output = SimAuto.ChangeParametersMultipleElement("Gen", \_

ParamList, ValueList) 

**[Python](#changeparametersmultipleelement-sample-code-for-python)**

---

<a id="changeparametersmultipleelement-sample-code-for-python"></a>

## ChangeParametersMultipleElement Sample Code for Python

*Source: [`Content/MainDocumentation_HTML/ChangeParametersMultipleElement_Sample_Code_Python.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ChangeParametersMultipleElement_Sample_Code_Python.htm)*

\#The following example uses Python 3.x syntax

\#Python with COM requires the pyWin32 extensions

import win32com.client

from win32com.client import VARIANT

\# This will import VT\_VARIANT

import pythoncom

\# This will establish the connection

object = win32com.client.Dispatch("pwrworld.SimulatorAuto")

\# The following function will determine if any errors are returned and print an appropriate message.

def CheckResultForError(SimAutoOutput, Message):

if SimAutoOutput\[0\] \!= '':

print ('Error: ' + SimAutoOutput\[0\])

else:

print (Message)

filename = "C:\\TestCode\\B7FLAT.pwb"

CheckResultForError(object.OpenCase(filename), 'Case open')

ObjectType = "GEN"

\#VARIANT is needed if passing in array of arrays. BOTH the field list

\#and the value list must use this syntax. If not passing in arrays of arrays, the

\#standard list format can be used. Passing out arrays of arrays from SimAuto in the

\#output parameter seems to work OK with Python.

FieldArray = VARIANT(pythoncom.VT\_VARIANT | pythoncom.VT\_ARRAY, \["BusNum", "ID", "MW", "AGC"\])

AllValueArray = \[None\]\*2

AllValueArray\[0\] = VARIANT(pythoncom.VT\_VARIANT | pythoncom.VT\_ARRAY, \[1, "1", 300, "NO"\])

AllValueArray\[1\] = VARIANT(pythoncom.VT\_VARIANT | pythoncom.VT\_ARRAY, \[2, "1", 1400, "NO"\])

CheckResultForError(object.ChangeParametersMultipleElement("GEN", FieldArray, AllValueArray), 'Do change')

filename = "C:\\TestCode\\B7FLAT\_changed.pwb"

CheckResultForError(object.SaveCase(filename,"PWB", True), 'Save case')

\#This will close the connection

del object

object = None

---

<a id="changeparametersmultipleelementflatinput"></a>

## ChangeParametersMultipleElementFlatInput

*Source: [`Content/MainDocumentation_HTML/ChangeParametersMultipleElementFlatInput_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ChangeParametersMultipleElementFlatInput_Function.htm)*

The ChangeParametersMultipleElementFlatInput function allows you to set parameters for multiple objects of the same type in a case loaded into the Simulator Automation Server. This function is very similar to the [ChangeParametersMultipleElement](#changeparametersmultipleelement), but uses a single dimensioned array of values as input instead of a multi-dimensioned array of arrays. The advantage of this function is that it is much faster to change multiple elements with a single function call than it is to repeatedly call [ChangeParametersSingleElement](#changeparameterssingleelement) multiple times. An additional advantage over ChangeParametersMultipleElement is that you can still take advantage of the speed improvement, even if the programming language you are using does not support multi-dimensioned arrays.

Unlike the script SetData and CreateData commands, SimAuto does not have any explicit functions to create elements. Instead this can be done using the ChangeParameters functions by making use of the [CreateIfNotFound](33-simauto-overview-and-setup.md#createifnotfound) SimAuto property. Set CreateIfNotFound = True if objects that are updated through the ChangeParameters functions should be created if they do not already exist in the case. Objects that already exist will be updated. Set CreateIfNotFound = False to not create new objects and only update existing ones. The CreateIfNotFound property is global, once it is set to True this applies to all future ChangeParameters calls.

**Function Prototype**

**ChangeParametersMultipleElementFlatInput(ObjectType, ParamList, NoOfObjects, ValueList)**

Parameter Definitions

**ObjectType : String **The type of object for which parameters are being changed.

**ParamList : Variant **A variant array storing strings (COM Type BSTR). This array stores a list of PowerWorldâ object field variables, as defined in the section on [PowerWorld Object Fields](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names). The ParamList must contain the [key field](04-model-explorer-and-case-information-part3.md#key-fields) variables for the specific device, or the device cannot be identified.

**NoOfObjects **You must pass an integer number of devices that are passing values for. SimAuto will automatically check that the number of parameters for each device (counted from ParamList) and the number of objects integer correspond to the number of values in value list (counted from ValueList.)

**ValueList : Variant **A variant array storing a list of variants. Value list can be an array with many values, as it is a single dimensioned array of all values for all devices that are being changed. The structure of the ValueList array is such that all of the parameters for the first object are listed first, then all parameters for the second object, and so on. The parameters must be in the same order as given in ParamList. In other words, your array would look like:  

ValueList = Array(Obj1Param1, Obj1Param2, Obj2Param1, Obj2Param2,Obj3Param1, …, ObjNParam1, ObjNParam2)

Output

ChangeParametersMultipleElementFlatInput only returns the first element in Output, the error string.

Notes

If the number of parameters given in ParamList multiplied by the number of objects passed does not equal the total number of values in ValueList, SimAuto will abort the function call.

---

<a id="changeparametersmultipleelementflatinput-sample-code"></a>

## ChangeParametersMultipleElementFlatInput Sample Code

*Source: [`Content/MainDocumentation_HTML/ChangeParametersMultipleElementFlatInput_Sample_Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ChangeParametersMultipleElementFlatInput_Sample_Code.htm)*

Borland® Delphi

Var ParamList, ValueList : OLEVariant

// Set ParamList up to modify the MW output of generators

ParamList := VarArrayCreate(\[1,3\], varOleStr);

ParamList\[1\] := 'BusNum';

ParamList\[2\] := 'ID';

ParamList\[3\] := ‘MW’;

// ValueList is setup with MW values for generators at buses 1 and 2

NumObjects := 2;

NumFields := NumObjects \* 3;

ValueList := VarArrayCreate(\[1,NumFields\], varOleStr);

For k := 0 to 1 do begin

ValueList\[3\*k+1\] := k;

ValueList\[3\*k+2\] := ‘1’;

ValueList\[3\*k+3\] := k\*10;

End;

// Make the ChangeParametersMultipleElementFlatInput call

Output = SimAuto.ChangeParametersMultipleElementFlatInput('Gen', \_

ParamList, NumObjects, ValueList)

Microsoft® Visual Basic for Applications

' Set ParamList up to modify the MW output of generators

Dim ParamList As Variant

ParamList = Array("BusNum", "ID", "MW")

' ValueList is setup with MW values for generators at buses 1 and 2

NumObjects = 2

NumFields = NumObjects \* 3

Dim ValueList(NumObjects) As Variant

For k = 0 to 1

ValueList(3\*k+1) = k

ValueList\[3\*k+2\] := ‘1’;

ValueList\[3\*k+3\] := k\*10;

Next

' Make the ChangeParametersMultipleElementFlatInput call

Output = SimAuto.ChangeParametersMultipleElementFlatInput("Gen", \_

ParamList, NumObjects, ValueList)

---

<a id="changeparametersmultipleelementrect"></a>

## ChangeParametersMultipleElementRect

*Source: [`Content/MainDocumentation_HTML/ChangeParametersMultipleElementRect_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ChangeParametersMultipleElementRect_Function.htm)*

The ChangeParametersMultipleElementRect function allows you to set parameters for multiple objects of the same type in a case loaded into the Simulator Automation Server. This function is very similar to the [ChangeParametersMultipleElement](#changeparametersmultipleelement) function call but uses a different structure for passing the values to change. The advantages of this function is that it is processed much faster and the input Values structure is easier to create in most programming languages.

Unlike the script SetData and CreateData commands, SimAuto does not have any explicit functions to create elements. Instead this can be done using the ChangeParameters functions by making use of the [CreateIfNotFound](33-simauto-overview-and-setup.md#createifnotfound) SimAuto property. Set CreateIfNotFound = True if objects that are updated through the ChangeParameters functions should be created if they do not already exist in the case. Objects that already exist will be updated. Set CreateIfNotFound = False to not create new objects and only update existing ones. The CreateIfNotFound property is global, once it is set to True this applies to all future ChangeParameters calls.

Function Prototype

**ChangeParametersMultipleElementRect(ObjectType, ParamList, Values)**

Parameter Definitions

**ObjectType : String **The type of object for which parameters are being changed.

**ParamList : Variant **A variant array storing strings. This array stores a list of PowerWorld object field variables, as defined in the section on [PowerWorld Object Fields](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names). The ParamList must contain the [key field](04-model-explorer-and-case-information-part3.md#key-fields) variables for the specific device, or the device cannot be identified.

**Values : Variant **Two-dimensional variant array containing variants. Each row represents an object with each column containing each field in the ParamList for that object. Each object is identified by the key fields that are in the ParamList.

The following figure shows the structure of the Values parameter:

![ChangeParametersMultipleElementRect Values 794x317](images/ChangeParametersMultipleElementRect_Values_794x317.jpg)

Output

ChangeParametersMultipleElementRect only returns the first element in Output, the error string.

---

<a id="closecase"></a>

## CloseCase

*Source: [`Content/MainDocumentation_HTML/CloseCase_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/CloseCase_Function.htm)*

The CloseCase function is used to close a load flow case loaded in the [Simulator Automation Server](33-simauto-overview-and-setup.md#automation-server). This function should be called at some point after the [OpenCase](#opencase) function.

Function Prototype

**CloseCase()**

Parameter Definitions

No parameters are passed.

Output

CloseClase returns only one element in Output—any errors which may have occurred when attempting to close the case.

---

<a id="closecase-sample-code"></a>

## CloseCase Sample Code

*Source: [`Content/MainDocumentation_HTML/CloseCase_Sample_Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/CloseCase_Sample_Code.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Borland® Delphi

Output := SimAuto.CloseCase();

Microsoft® Visual Basic for Applications

Output = SimAuto.CloseCase()

Matlab®

Output = SimAuto.CloseCase

---

<a id="getcaseheader"></a>

## GetCaseHeader

*Source: [`Content/MainDocumentation_HTML/GetCaseHeader_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetCaseHeader_Function.htm)*

The GetCaseHeader function is used to extract the case header information from the specified file.

Function Prototype

**GetCaseHeader("filename");** 

Parameter Definitions

**"filename" : String **The name of the file from which to extract the header information.

Output

Output(0) — error string

Output(1) — variant array of variant strings containing the contents of the case header

---

<a id="getfieldlist"></a>

## GetFieldList

*Source: [`Content/MainDocumentation_HTML/GetFieldList_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetFieldList_Function.htm)*

The GetFieldList function is used to find all fields contained within a given object type.

Function Prototype

**GetFieldList(ObjectType)**

Parameter Definitions

**ObjectType : String** The type of object for which the fields are requested.

Output

GetFieldList returns two elements of the Output array. The first element returns any errors that might have occurred. The second element of the Output array contains an n x 6 array of fields. The layout of this array is virtually identical to the output obtained by going to **Window \> Export Case Object Fields** from the main menu of Simulator.

Output(1)(n,0) - specifies which fields are key fields for the object by using numbers to indicate primary keys and letters to indicate secondary keys

Output(1)(n,1) - variablename:location (this is always the legacy variablename)

Output(1)(n,2) - type of data stored in the field (e.g., String, Integer, Real)

Output(1)(n,3) - field description

Output(1)(n,4) - concise variablename:location

Output(1)(n,5) - enterable (will be blank if the field is not enterable, Yes if enterable, or will contain an explanation if conditionally enterable) Added in version 22, build on November 18, 2021

---

<a id="getfieldlist-sample-code"></a>

## GetFieldList Sample Code

*Source: [`Content/MainDocumentation_HTML/GetFieldList_Sample_Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetFieldList_Sample_Code.htm)*

Microsoft® Visual Basic for Applications

Dim objecttype As String

' Object type to obtain

objecttype = "branch"

' Make the GetField call

Output = SimAuto.GetFieldList(objecttype)

Matlab®

% Object type to obtain

objecttype = 'branch';

% Make the GetField call

Output = SimAuto.GetFieldList(objecttype);

---

<a id="getparameterssingleelement"></a>

## GetParametersSingleElement

*Source: [`Content/MainDocumentation_HTML/GetParametersSingleElement_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetParametersSingleElement_Function.htm)*

The GetParametersSingleElement function is used to request the values of specified fields for a particular object in the load flow case. For returning field values for multiple objects, you can use a loop to make repeated calls to the GetParametersSingleElement function, and pass the object and desired field information for each object. This function is identical in setup to the [ChangeParameters](52-additional-linked-topics-part1.md#changeparameters-function) function, with the exception that the Values array will be updated with the values for the field variables defined in ParamList.

Function Prototype

**GetParametersSingleElement(ObjectType, ParamList, Values)**

Parameter Definitions

**ObjectType : String **The type of object for which parameters are being changed

**ParamList : Variant **A variant array storing strings. This array stores a list of PowerWorldâ object field variables, as defined in the section on [PowerWorld Object Fields](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names). The ParamList must contain the [key field](04-model-explorer-and-case-information-part3.md#key-fields) variables or [label](07-object-properties-run-mode-and-general-part2.md#labels) for the specific device, or the device cannot be identified. The remaining field variables in the array define which values to retrieve from Simulator.

**Values : Variant **A variant array storing variants. This array can store any type of information (integer, string, etc.) in each array position. Values must be passed for the [key field](04-model-explorer-and-case-information-part3.md#key-fields) variables in ParamList, in the same array position. The remaining field positions in the Values array should be set to zero.

Output

The output is a variant array:

Output(0) — error string

Output(1) — one-dimensional array containing the values corresponding to the fields specified in ParamList

Output Structure

The Output structure of GetParametersSingleElement is shown in the following figure:

![GetParametersSingleElement 519x190](images/GetParametersSingleElement_519x190.png)

---

<a id="getparameterssingleelement-sample-code-delphi"></a>

## GetParametersSingleElement Sample Code Delphi

*Source: [`Content/MainDocumentation_HTML/GetParametersSingleElement_Sample_Code_Delphi.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetParametersSingleElement_Sample_Code_Delphi.htm)*

// This example retrieves some parameters for bus 2 of the loaded

// case, using the GetParametersSingleElement function, as well as

// the old GetParameters function

procedure TMainForm.RunGPSEClick(Sender: TObject);

var

Output : OLEVariant; 

FieldBusArray, ValueBusArray : OLEVariant; 

i : Integer; 

begin

// Declares fields array to be sent to Excel 

FieldBusArray := VarArrayCreate(\[1,5\], varOleStr); 

FieldBusArray\[1\] := 'Number'; 

FieldBusArray\[2\] := 'Name'; 

FieldBusArray\[3\] := 'kV'; 

FieldBusArray\[4\] := 'Vpu'; 

FieldBusArray\[5\] := 'Vangle'; 

ValueBusArray := varArrayCreate(\[1,5\],varOleStr); 

ValueBusArray\[1\] := 2; // To get parameters for bus 2 

ValueBusArray\[2\] := 0; 

ValueBusArray\[3\] := 0; 

ValueBusArray\[4\] := 0; 

ValueBusArray\[5\] := 0; 

// Gets parameters with GetParametersSingleElement function 

Output := SimAuto.GetParametersSingleElement('bus', FieldBusArray, ValueBusArray); 

if (string(Output\[0\]) \<\> '') then 

StatusBar1.Panels\[1\].Text := 'Error: ' + string(Output\[0\]) 

else 

begin 

StatusBar1.Panels\[1\].Text := 'Parameters got.'; 

Memo1.Lines.Add('== GetParametersSingleElement =='); 

Memo1.Lines.Add('Value : Output\[1\]\[i\]'); 

for i := VarArrayLowBound(Output\[1\],1) to VarArrayHighBound(Output\[1\],1) do begin 

Memo1.Lines.Add(FieldBusArray\[i\] + ' : ' + string(Output\[1\]\[i\])); 

end; 

Memo1.Lines.Add(''); 

end; 

// Gets parameters with old function GetParameters 

Output := SimAuto.GetParameters('bus', FieldBusArray, ValueBusArray); 

if (string(Output\[0\]) \<\> '') then 

StatusBar1.Panels\[1\].Text := 'Error: ' + string(Output\[0\]) 

else 

begin 

StatusBar1.Panels\[1\].Text := 'Parameters got.'; 

Memo1.Lines.Add('== GetParameters =='); 

Memo1.Lines.Add('Value : Output\[1\]\[i\]'); 

for i := VarArrayLowBound(Output\[1\],1) to VarArrayHighBound(Output\[1\],1) do begin 

Memo1.Lines.Add(FieldBusArray\[i\] + ' : ' + string(Output\[1\]\[i\])); 

end; 

Memo1.Lines.Add(''); 

end; 

end;

---

<a id="getparameterssingleelement-sample-code-matlab"></a>

## GetParametersSingleElement Sample Code Matlab

*Source: [`Content/MainDocumentation_HTML/GetParametersSingleElement_Sample_Code_Matlab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetParametersSingleElement_Sample_Code_Matlab.htm)*

% This example loads all buses in the case, and then gets

% some parameters of the last bus in the list

% validcase is a global variable – check case is open

if validcase

% Gets all buses in the case 

output = simauto.ListOfDevices('bus',''); 

if \~(strcmp(output{1},'')) 

disp(output{1}) 

validbusarray = false; 

else 

% Puts the buses in row vector busarray 

for i=size(output{2}{1},1):size(output{2}{1},2) 

busarray(i,1) = output{2}{1}(i);  

end 

disp('Succesful ListOfDevices') 

disp(busarray) 

validbusarray = true; 

end 

end

% validbusarray is a global variable – check buses are loaded

if validcase & validbusarray

% Gets parameters for last bus of busarray 

fieldarray = {'Number' 'Name' 'Vpu' 'Vangle'}; 

valuearray = \[busarray(size(busarray,1)) '0' '0' '0'\]; 

valuelist = num2cell(valuearray); 

output = simauto.GetParametersSingleElement('bus',fieldarray,valuelist); 

if \~(strcmp(output{1},'')) 

disp(output{1}) 

else 

% Puts the buses in row vector busparam 

paramlist = transpose(output{2}); 

for i=size(paramlist,1):size(paramlist,2) 

busparam(i,1) = paramlist(i);  

end 

disp('Succesful GetParameters for Bus') 

disp(fieldarray) 

disp(busparam) 

end 

end

---

<a id="getparameterssingleelement-sample-code-vb"></a>

## GetParametersSingleElement Sample Code VB

*Source: [`Content/MainDocumentation_HTML/GetParametersSingleElement_Sample_Code_VB.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetParametersSingleElement_Sample_Code_VB.htm)*

Private Sub btnGetParametersSingleElement\_Click()

Dim objtype, filter As String

Dim xlWB As Excel.Workbook

Set xlApp = Excel.Application

' Checks connection and open case

' SimAuto and caseopen are global variables

If Not SimAuto Is Nothing And caseopen Then

objtype = "bus" 

Dim fieldArray As Variant 

fieldArray = Array("Number", "Name", "kV", \_ 

"Vpu", "Vangle") 

Dim ValueArray As Variant 

ValueArray = Array(1, 0, 0, 0, 0) 

output = SimAuto.GetParametersSingleElement(objtype, fieldArray, ValueArray) 

If output(0) \<\> "" Then 

DisplayErrorMessage output(0) 

Else 

DisplayMessage "Succesful GetParametersSingleElement" 

' Prepares additional worksheet 

Set xlWB = xlApp.Workbooks.Add 

' Copies list of devices in worksheet 

With xlWB 

Sheets("sheet2").Activate 

Sheets("sheet2").Name = "GetParametersSingleElement" 

With Sheets("GetParametersSingleElement") 

Dim i As Integer 

Range(Cells(1, 5), Cells(200, 7)).Clear 

Cells(1, 1) = "List of Devices for " + objtype + ":" 

' Setup fields as subheader 

For i = LBound(fieldArray) To UBound(fieldArray) 

Cells(2, i + 1) = fieldArray(i) 

Next i 

' Determine number of fields retrieved 

Dim lowfld, highfld As Integer 

lowfld = LBound(output(1), 1) 

highfld = UBound(output(1), 1) 

DisplayMessage "Number of Fields: " + Str(lowfld) + Str(highfld) 

For i = lowfld To highfld 

Cells(j + 3, i + 1) = output(1)(i) 

Next i 

End With 

End With 

End If 

End If

End Sub

---

<a id="getparametersmultipleelement"></a>

## GetParametersMultipleElement

*Source: [`Content/MainDocumentation_HTML/GetParametersMultipleElement_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetParametersMultipleElement_Function.htm)*

The GetParametersMultipleElement function is used to request the values of specified fields for a set of objects in the load flow case. The function can return values for all devices of a particular type, or can return values for only a list of devices of a particular type based on a filter defined for the loaded case.

Function Prototype

**GetParametersMultipleElement(ObjectType, ParamList, Filter)**

Parameter Definitions

**ObjectType : String **The type of object for which parameters are being retrieved.

**ParamList : Variant **A variant array storing strings. This array stores a list of PowerWorldâ object field variables, as defined in the section on [PowerWorld Object Variables](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names), for the values to retrieve from Simulator.

**Filter : String **The name of an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering), a device filter, or a single-condition filter. If no filter is desired, simply pass an empty string. An error will be returned if a named filter cannot be found, device cannot be found for a device filter, or a single-condition filter is in the wrong format.

Output

When [Difference Case Tools and DiffCaseMode = Change](08-view-case-data-tools.md#difference-case), then using the various get parameters calls will only return objects that have input parameters specified that have at least one non-key field that has changed (this was added in Version 23 patch on June 25, 2024.)

The output is a variant array:

Output(0) — error string

Output(1) — set of nested arrays containing the parameter values for the device type requested. The number of arrays of values returned depends on the number of fields in ParamList.

Output Structure

The Output structure of GetParametersMultipleElement is shown in the following figure:

![GetParametersMultipleElement 776x316](images/GetParametersMultipleElement_776x316.png)

As you can see, to access the first parameter value for the first device, Output\[1\]\[0\]\[0\] would be the correct array index. For example, the bus number for the first bus would be stored at Output\[1\]\[0\]\[0\] after calling Output = GetParametersMultipleElement('Bus',fieldarray, ''), and assuming that we have fieldarray = Array('Number', 'Name').

---

<a id="getparametersmultipleelement-sample-code-delphi"></a>

## GetParametersMultipleElement Sample Code Delphi

*Source: [`Content/MainDocumentation_HTML/GetParametersMultipleElement_Sample_Code_Delphi.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetParametersMultipleElement_Sample_Code_Delphi.htm)*

// This example retrieves some parameters for all buses of the

// loaded case, using the GetParametersMultipleElement function

procedure TMainForm.RunGPMEClick(Sender: TObject);

var

FieldBusArray : OLEVariant; 

i,j : Integer; 

begin

// Declares fields array to be sent to Excel 

FieldBusArray := VarArrayCreate(\[1,5\], varOleStr); 

FieldBusArray\[1\] := 'Number'; 

FieldBusArray\[2\] := 'Name'; 

FieldBusArray\[3\] := 'kV'; 

FieldBusArray\[4\] := 'Vpu'; 

FieldBusArray\[5\] := 'Vangle'; 

// Gets parameters with Multiple Element function 

Output := SimAuto.GetParametersMultipleElement('bus', FieldBusArray, ''); 

if (string(Output\[0\]) \<\> '') then 

StatusBar1.Panels\[1\].Text := 'Error: ' + string(Output\[0\]) 

else 

begin 

StatusBar1.Panels\[1\].Text := 'Parameters got.'; 

Memo1.Lines.Add('== GetParametersMultipleElement =='); 

Memo1.Lines.Add('Value : Output\[1\]\[i\]\[j\]'); 

for i := VarArrayLowBound(Output\[1\],1) to VarArrayHighBound(Output\[1\],1) do begin 

for j := VarArrayLowBound(Output\[1\]\[i\],1) to VarArrayHighBound(Output\[1\]\[i\],1)  

do begin 

Memo1.Lines.Add(FieldBusArray\[i\] + '(' + IntToStr(j) + ') : ' +  

string(Output\[1\]\[i\]\[j\])); 

end; 

end; 

Memo1.Lines.Add(''); 

end; 

end;

---

<a id="getparametersmultipleelement-sample-code-matlab"></a>

## GetParametersMultipleElement Sample Code Matlab

*Source: [`Content/MainDocumentation_HTML/GetParametersMultipleElement_Sample_Code_Matlab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetParametersMultipleElement_Sample_Code_Matlab.htm)*

% This example loads all buses in the case, and then gets

% some parameters of such buses

% validcase is a global variable – check case is open

if validcase

% Gets all buses in the case 

output = simauto.ListOfDevices('bus', ''); 

if \~(strcmp(output{1},'')) 

disp(output{1}) 

validbusarray = false; 

else 

% Puts the buses in row vector busarray 

for i=size(output{2}{1},1):size(output{2}{1},2) 

busarray(i,1) = output{2}{1}(i);  

end 

disp('Succesful ListOfDevices') 

disp(busarray) 

validbusarray = true; 

end 

end

% validbusarray is a global variable – check buses are loaded

if validcase & validbusarray

% Gets parameters for all buses 

fieldarray = {'Number' 'Name' 'Vpu' 'Vangle'}; 

output = simauto.GetParametersMultipleElement('bus', fieldarray,' '); 

if \~(strcmp(output{1},'')) 

disp(output{1}) 

else 

% Puts the buses in matrix busesparam 

paramlist = transpose(output{2}); 

for i=size(paramlist,1):size(paramlist,2) 

for j=size(paramlist{i},2):size(paramlist{i},1) 

busesparam(j,i) = paramlist{i}(j); 

end 

end 

disp('Succesful GetParametersMultipleElement') 

disp(fieldarray) 

disp(busesparam) 

end 

end

---

<a id="getparametersmultipleelement-sample-code-vb"></a>

## GetParametersMultipleElement Sample Code VB

*Source: [`Content/MainDocumentation_HTML/GetParametersMultipleElement_Sample_Code_VB.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetParametersMultipleElement_Sample_Code_VB.htm)*

Private Sub btnGetParametersMultiple\_Click()

Dim objtype, filter As String

Dim xlWB As Excel.Workbook

Set xlApp = Excel.Application

' Checks connection and open case

' SimAuto and caseopen are global variables

If Not SimAuto Is Nothing And caseopen Then

objtype = "bus" 

filter = "" 

Dim fieldArray As Variant 

fieldArray = Array("Number", "Name", "kV", \_ 

"Vpu", "Vangle") 

output = SimAuto.GetParametersMultipleElement(objtype, fieldArray, filter) 

If output(0) \<\> "" Then 

DisplayErrorMessage output(0) 

Else 

DisplayMessage "Succesful GetParametersSingleElement" 

' Prepares additional worksheet 

Set xlWB = xlApp.Workbooks.Add 

' Copies list of devices in worksheet 

With xlWB 

Sheets("sheet2").Activate 

Sheets("sheet2").Name = "GetParametersSingleElement" 

With Sheets("GetParametersSingleElement") 

Dim i, j As Integer 

Range(Cells(1, 5), Cells(200, 7)).Clear 

Cells(1, 1) = "List of Devices for " + objtype + ":" 

' Setup fields as subheader 

For i = LBound(fieldArray) To UBound(fieldArray) 

Cells(2, i + 1) = fieldArray(i) 

Next i 

' Determine number of fields retrieved 

Dim lowfld, highfld As Integer 

lowfld = LBound(output(1), 1) 

highfld = UBound(output(1), 1) 

' Determine number of objects retrieved 

Dim lowobj, highobj As Integer 

lowobj = LBound(output(1)(lowkeyf), 1) 

highobj = UBound(output(1)(lowkeyf), 1) 

DisplayMessage "Number of Fields: " + Str(lowfld) + Str(highfld) 

DisplayMessage "Number of objects: " + Str(lowobj) + Str(highobj) 

For i = lowfld To highfld 

For j = lowobj To highobj 

Cells(j + 3, i + 1) = output(1)(i)(j) 

Next j 

Next i 

End With 

End With 

End If 

End If

End Sub

---

<a id="getparametersmultipleelementflatoutput"></a>

## GetParametersMultipleElementFlatOutput

*Source: [`Content/MainDocumentation_HTML/GetParametersMultipleElementFlatOutput_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetParametersMultipleElementFlatOutput_Function.htm)*

This function operates the same as the [GetParametersMultipleElement](#getparametersmultipleelement) function, only with one notable difference. The values returned as the output of the function are returned in a single-dimensional vector array, instead of the multi-dimensional array as described in the GetParametersMultipleElement topic. The function returns the parameter values for the device type requested, and the number of values returned depends on the ParamList and any [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) that impacts the number of devices returned.

The format of the output array is the following:

\[errorString, NumberOfObjectsReturned, NumberOfFieldsPerObject, Ob1Fld1, Ob1Fld2, …, Ob(n)Fld(m-1), Ob(n)Fld(m)\]

The data is thus returned in a single dimension array, where the parameters NumberOfObjectsReturned and NumberOfFieldsPerObject tell you how the rest of the array is populated. Following the NumberOfObjectsReturned parameter is the start of the data. The data is listed as all fields for object 1, then all fields for object 2, and so on. You can parse the array using the NumberOf… parameters for objects and fields.

When [Difference Case Tools and DiffCaseMode = Change](08-view-case-data-tools.md#difference-case), then using the various get parameters calls will only return objects that have input parameters specified that have at least one non-key field that has changed (this was added in Version 23 patch on June 25, 2024.)

---

<a id="getparametersmultipleelementrect"></a>

## GetParametersMultipleElementRect

*Source: [`Content/MainDocumentation_HTML/GetParametersMultipleElementRect_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetParametersMultipleElementRect_Function.htm)*

The GetParametersMultipleElementRect function is used to request the values of specified fields for a set of objects in the case. The function can return values for all devices of a particular type, or can return values for only a list of devices of a particular type based on a filter defined for the loaded case. This function is similar to the [GetParametersMultipleElement](#getparametersmultipleelement) function but has the advantages of being much faster and the output structure being easier to process in most programming languages.

Function Prototype

**GetParametersMultipleElementRect(ObjectType, ParamList, Filter)**

Parameter Definitions

**ObjectType : String **The type of object for which parameters are being retrieved

**ParamList : Variant **A variant array storing strings. This array stores a list of PowerWorldâ object field variables, as defined in the section on [PowerWorld Object Variables](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names), for the values to retrieve from Simulator.

**Filter : String **The name of an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering), a device filter, or a single-condition filter. If no filter is desired, simply pass an empty string. An error will be returned if a named filter cannot be found, device cannot be found for a device filter, or a single-condition filter is in the wrong format.

Output

When [Difference Case Tools and DiffCaseMode = Change](08-view-case-data-tools.md#difference-case), then using the various get parameters calls will only return objects that have input parameters specified that have at least one non-key field that has changed (this was added in Version 23 patch on June 25, 2024.)

The output is a variant array:

Output(0) — error string

Output(1) — Two-dimensional variant array containing variants with each row representing an object and the corresponding columns representing each field in ParamList for that object.

Output Structure

The Output structure of GetParametersMultipleElementRect is shown in the following figure:

![GetParametersMultipleElementRect 784x390](images/GetParametersMultipleElementRect_784x390.png)

---

<a id="getparamsrecttyped"></a>

## GetParamsRectTyped

*Source: [`Content/MainDocumentation_HTML/GetParamsRectTyped_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetParamsRectTyped_Function.htm)*

The GetParamsRectTyped function is used to request the values of specified fields of a specified type for a set of objects in the case. The fields that are returned must all be convertible to the specified type. This function is similar to the [GetParametersMultipleElementRect](#getparametersmultipleelementrect) function but has the advantage of specifying the data type of the returned fields rather than returning all values as strings.

Function Prototype

**GetParamsRectTyped(ObjectType, ParamList, Filter, ValueType)**

Parameter Definitions

**ObjectType : String **The type of object for which parameters are being retrieved

**ParamList : Variant **A variant array storing strings. This array stores a list of PowerWorldâ object field variables, as defined in the section on [PowerWorld Object Variables](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names), for the values to retrieve from Simulator.

**Filter : String **The name of an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering), a device filter, or a single-condition filter. If no filter is desired, simply pass an empty string. An error will be returned if a named filter cannot be found, device cannot be found for a device filter, or a single-condition filter is in the wrong format.

**ValueType : VARENUM type** Enumerated type representing supported variant type. The supported types are VT\_I2, VT\_I4, VT\_R4, VT\_R8, VT\_BSTR, and VT\_VARIANT. The values for all fields must be convertible to this type. For example it is invalid to retrieve a branch status field as an integer or float, but it is valid to retrieve a numerical field into a string or variant array.

Output

When [Difference Case Tools and DiffCaseMode = Change](08-view-case-data-tools.md#difference-case), then using the various get parameters calls will only return objects that have input parameters specified that have at least one non-key field that has changed.

The output is a variant array:

Output(0) — error string

Output(1) — Two-dimensional array with each row representing an object and the corresponding columns representing each field in ParamList for that object returned as the specified ValueType

Output Structure

The Output structure is shown in the following figure:

![GetParametersMultipleElementRect 787x389](images/GetParametersMultipleElementRect_787x389.png)

---

<a id="getparamsrecttyped-sample-code-python"></a>

## GetParamsRectTyped Sample Code Python

*Source: [`Content/MainDocumentation_HTML/GetParamsRectTyped_Sample_Code_Python.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetParamsRectTyped_Sample_Code_Python.htm)*

\#The following example uses Python 3.x syntax

\#Python with COM requires the pyWin32 extensions

import win32com.client

\# This will import VT\_VARIANT

import pythoncom

\# This will establish the connection

object = win32com.client.Dispatch("pwrworld.SimulatorAuto")

\# The following function will determine if any errors are returned and print an appropriate message.

def CheckResultForError(SimAutoOutput, Message):

if SimAutoOutput\[0\] \!= '':

print ('Error: ' + SimAutoOutput\[0\])

else:

print (Message)

filename = "B7FLAT.pwb"

CheckResultForError(object.OpenCase(filename), 'Case open')

\# The following will result in an error because ID and AreaName are strings that cannot be converted to a floating point number.

FieldArray = \["BusNum", "ID", "GenMW", "AreaName"\]

output = object.GetParamsRectTyped("GEN", FieldArray, "", pythoncom.VT\_R8)

CheckResultForError(output, 'Get Typed')

\# Results in error *Unsupported conversion of non-scalar field ID to a non-VT\_BSTR type.*

\# Would also result in error for field AreaName if ID field is removed.

\# The following will NOT result in an error because results are returned as variants.

FieldArray = \["BusNum", "ID", "GenMW", "AreaName"\]

output = object.GetParamsRectTyped("GEN", FieldArray, "", pythoncom.VT\_VARIANT)

CheckResultForError(output, 'Get Typed')

\# The following will return results without an error because both fields can be converted to floating point values.

\# Filter is written as a single-condition filter that returns the generators at Bus 1.

FieldArray = \["BusNum", "GenMW"\]

output = object.GetParamsRectTyped("GEN", FieldArray, "BusNum = 1", pythoncom.VT\_R8)

CheckResultForError(output, 'Get Typed')

\#This will close the connection

del object

object = None

---

<a id="getparamstypedcols"></a>

## GetParamsTypedCols

*Source: [`Content/MainDocumentation_HTML/GetParamsTypedCols_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetParamsTypedCols_Function.htm)*

The GetParamsTypedCols function is used to request the values of specified fields of a specified type for a set of objects in the case. The fields that are returned must all be convertible to the specified type. This function is similar to the [GetParamsRectTyped](#getparamsrecttyped) function but has the advantage of being able to specify the data type of each different returned field. The structure of the output is similar to [GetParametersMultipleElement](#getparametersmultipleelement).

Function Prototype

**GetParametersTypedCols(ObjectType, ParamList, Filter, ColTypes)**

Parameter Definitions

**ObjectType : String **The type of object for which parameters are being retrieved

**ParamList : Variant **A variant array storing strings. This array stores a list of PowerWorldâ object field variables, as defined in the section on [PowerWorld Object Variables](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names), for the values to retrieve from Simulator.

**Filter : String **The name of an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering), a device filter, or a single-condition filter. If no filter is desired, simply pass an empty string. An error will be returned if a named filter cannot be found, device cannot be found for a device filter, or a single-condition filter is in the wrong format.

**ColTypes : VARENUM type or Array of VARENUM types** VARENUM type is an enumerated type representing supported variant types: VT\_I2, VT\_I4, VT\_R4, VT\_R8, VT\_BSTR, and VT\_VARIANT. If all fields to be returned are of the same type, only a single VARENUM value may be specified. If each field is of a different type, pass an array of the same dimension as ParamList with the specified type index corresponding to the field index in the ParamList for the desired field type. The values for all fields must be convertible to the specified type. For example it is invalid to retrieve a branch status field as an integer or float, but it is valid to retrieve a numerical field into a string or variant array.

If the type is specified as VT\_VARIANT, the resulting value array will contain variants of VT\_I4, VT\_R8, or VT\_BSTR depending on whether the column is an integer field, a floating point field, or a field of any other type represented by a string.

Output

When [Difference Case Tools and DiffCaseMode = Change](08-view-case-data-tools.md#difference-case), then using the various get parameters calls will only return objects that have input parameters specified that have at least one non-key field that has changed.

The output is a variant array:

Output(0) — error string

Output(1) — set of nested arrays containing the parameter values for the device type requested. The number of arrays of values returned depends on the number of fields in ParamList. The values will be returned as the specified ColTypes.

Output Structure

The Output structure of GetParamsTypedCols is shown in the following figure:

![GetParametersMultipleElement 776x316](images/GetParametersMultipleElement_776x316.png)

---

<a id="getparamstypedcols-sample-code-python"></a>

## GetParamsTypedCols Sample Code Python

*Source: [`Content/MainDocumentation_HTML/GetParamsTypedCols_Sample_Code_Python.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetParamsTypedCols_Sample_Code_Python.htm)*

\#The following example uses Python 3.x syntax

\#Python with COM requires the pyWin32 extensions

import win32com.client

\# This will import VT\_VARIANT

import pythoncom

\# This will establish the connection

object = win32com.client.Dispatch("pwrworld.SimulatorAuto")

\# The following function will determine if any errors are returned and print an appropriate message.

def CheckResultForError(SimAutoOutput, Message):

if SimAutoOutput\[0\] \!= '':

print ('Error: ' + SimAutoOutput\[0\])

else:

print (Message)

filename = "B7FLAT.pwb"

CheckResultForError(object.OpenCase(filename), 'Case open')

\# The following will result in an error because ID and AreaName are strings that cannot be converted to a floating point number.

FieldArray = \["BusNum", "ID", "GenMW", "AreaName"\]

output = object.GetParamsTypedCols("GEN", FieldArray, "", pythoncom.VT\_R8)

CheckResultForError(output, 'Get Typed All Same')

\# Results in error *Unsupported conversion of non-scalar field ID to VT\_R8.*

\# Would also result in error for field AreaName if ID field is removed.

\# The following will return results without an error because appropriate type for each field is specified.

FieldArray = \["BusNum", "ID", "GenMW", "AreaName"\]

ColTypesArray = \[pythoncom.VT\_I4, pythoncom.VT\_BSTR, pythoncom.VT\_R8, pythoncom.VT\_BSTR\]

output = object.GetParamsTypedCols("GEN", FieldArray, "", ColTypesArray)

CheckResultForError(output, 'Get Typed Each Specified')

\# Filter is written as a single-condition filter that returns the generators at Bus 1.

FieldArray = \["BusNum", "ID", "GenMW", "AreaName"\]

ColTypesArray = \[pythoncom.VT\_I4, pythoncom.VT\_BSTR, pythoncom.VT\_R8, pythoncom.VT\_BSTR\]

output = object.GetParamsTypedCols("GEN", FieldArray, "BusNum = 1", ColTypesArray)

CheckResultForError(output, 'Get Typed Using Single-condition Filter')

\# The following will NOT result in an error because results are returned as variants.

FieldArray = \["BusNum", "ID", "GenMW", "AreaName"\]

output = object.GetParamsTypedCols("GEN", FieldArray, "", pythoncom.VT\_VARIANT)

CheckResultForError(output, 'Get Typed Using VT\_VARIANT')

\#This will close the connection

del object

object = None

---

<a id="getspecificfieldlist"></a>

## GetSpecificFieldList

*Source: [`Content/MainDocumentation_HTML/GetSpecificFieldList_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetSpecificFieldList_Function.htm)*

The GetSpecificFieldList function is used to return identifying information about specific fields used by an object type.

Function Prototype

**GetSpecificFieldList(ObjectType, FieldList)**

Parameter Definitions

**ObjectType : String **The type of object for which fields are requested.

**FieldList : Variant **A variant array storing strings. This array stores a list of object field variables, as defined in the section on [PowerWorld Object Fields](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names). Specific variablenames along with location numbers can be specified. To return all fields using the same variablename, use "*variablename*:ALL" instead of the location number that would normally appear after the colon. If all fields should be returned, a single parameter of "ALL" can be used instead of specific variablenames.

Output

GetSpecificFieldList returns a two dimensional variant array. The first dimension, Output(0) contains the error string. The second dimension, Output(1), is a rectangular array indexed from 0 with a size of n x 5 where n is the number of fields that are returned. The specific information that is returned is as follows:

Output(1)(n,0) - variablename:location (this will either be the legacy or concise variablename depending on option settings)

Output(1)(n,1) - field (this is the identifier that is displayed when looking through the list of available fields for an object in a case information display in the GUI)

Output(1)(n,2) - column header (this is the column header that appears in a case information display in the GUI)

Output(1)(n,3) - field description

Output(1)(n,4) - enterable (will be blank if the field is not enterable, Yes if enterable, or will contain an explanation if conditionally enterable) Added in version 22, build on November 19, 2021

---

<a id="getspecificfieldmaxnum"></a>

## GetSpecificFieldMaxNum

*Source: [`Content/MainDocumentation_HTML/GetSpecificFieldMaxNum_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetSpecificFieldMaxNum_Function.htm)*

The GetSpecificFieldMaxNum function is used to return the maximum number of a fields that use a particular variablename for a specific object type.

Function Prototype

**GetSpecificFieldMaxNum(ObjectType, Field)**

Parameter Definitions

**ObjectType : String **The type of object for which information is being requested.

**Field : String** The variablename for which the maximum number of fields is being requested. This should just be the variablename and should exclude the location number that can be included to indicate different fields that use the same variablename, i.e. do not include the colon and number that can be included when identifying a field.

Output

An integer that specifies the maximum number of fields that use the same variablename for a particular object type. Fields are identified in the format variablename:location when multiple fields use the same variablename. The output indicates the maximum number that the location can be. Generally, fields are identified starting from 0 and going up to the maximum number, but keep in mind that values within this range might be skipped and not used to indicate valid fields.

---

<a id="listofdevices"></a>

## ListOfDevices

*Source: [`Content/MainDocumentation_HTML/ListOfDevices_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ListOfDevices_Function.htm)*

The ListOfDevices function is used to request a list of objects and their [key fields](04-model-explorer-and-case-information-part3.md#key-fields) from the [Simulator Automation Server](33-simauto-overview-and-setup.md#automation-server). The function can return all devices of a particular type, or can return only a list of devices of a particular type based on an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) defined for the loaded case. This function is best used in conjunction with a looping procedure and the [ChangeParameters](52-additional-linked-topics-part1.md#changeparameters-function) or [GetParametersSingleElement](#getparameterssingleelement) functions to process a group of devices.

Function Prototype

**ListOfDevices(ObjType, filterName)**

Parameter Definitions

**ObjType : String **The type of object for which you are acquiring the list of devices.

**Filter : String **The name of an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering), a device filter, or a single-condition filter. If no filter is desired, simply pass an empty string. An error will be returned if a named filter cannot be found, device cannot be found for a device filter, or a single-condition filter is in the wrong format.

Output

The output is a variant array:

Output(0) — error string

Output(1) — set of nested arrays containing the [key field](04-model-explorer-and-case-information-part3.md#key-fields) values for the device type requested. The number of arrays of values returned depends on the object type selected. For instance, buses have only one key field (the bus number) so calling ListOfDevices for buses will return only one array of values—the bus numbers. On the other hand, calling ListOfDevices for branches will return three arrays of values—the "From" bus, "To" bus, and ID—for each branch in the case meeting the specified filter.

Output Structure

The arrays containing the key field values for each device are arranged as shown in the following figure:

![ListOfDevices 695x337](images/ListOfDevices_695x337.png)

As you can see, to access the first key field value for the first device, Output\[1\]\[0\]\[0\] would be the correct array index. For example, the bus number (which is the bus key field) for the first bus would be stored at Output\[1\]\[0\]\[0\] after calling `Output = ListOfDevices('Bus', '')`.

One unique limitation of the ListOfDevices function from other SimAuto functions is that this is the only function that returns the output as strongly typed variables. The bus numbers are always returned as Long Integers, and the Circuit ID values are returned as strings. This was actually an oversight during the design of SimAuto. In all other SimAuto functions, the values are returned as Variant types, with each value within the variant being a string. This was the intended operation for this function as well. Since the Automation Server interface was released with the errant inclusion of the ListOfDevices function, it could not be modified. Therefore, another function, ListOfDevicesAsVariantStrings, has been created. This function returns all values in variant variables, with each as a string within the variant type.

---

<a id="listofdevices-sample-code-delphi"></a>

## ListOfDevices Sample Code Delphi

*Source: [`Content/MainDocumentation_HTML/ListOfDevices_Sample_Code_Delphi.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ListOfDevices_Sample_Code_Delphi.htm)*

Sample Code

// Runs Available Transfer Capability Routine

// Executes ATC Calculations among all areas

// and sends results to Excel

procedure TMainForm.RunATCClick(Sender: TObject);

var

i, j, LowB, HighB : Integer; 

ValuesAreaArray : OLEVariant; 

begin

// Obtain all the areas 

Output := SimAuto.ListOfDevices('area', ''); 

if (string(Output\[0\]) \<\> '') then 

StatusBar1.Panels\[1\].Text := 'Error: ' + string(Output\[0\]) 

else 

begin 

ValuesAreaArray := Output\[1\]\[0\]; 

LowB := VarArrayLowBound(ValuesAreaArray, 1); 

HighB := VarArrayHighBound(ValuesAreaArray, 1); 

// Executes loop 

for i := LowB to HighB do 

for j := LowB to HighB do begin 

if (i \<\> j) then begin 

// Runs ATC calculations 

OutputATC := SimAuto.RunScriptCommand('entermode(atc); ' +  

'atcdetermine(\[Area ' + IntToStr(ValuesAreaArray\[i\]) +  

'\], \[Area ' + IntToStr(ValuesAreaArray\[j\]) + '\])'); 

if (string(OutputATC\[0\]) \<\> '') then 

StatusBar1.Panels\[1\].Text := 'Error: ' + string(OutputATC\[0\]) 

else begin 

// Sends ATC results to Excel 

Output := SimAuto.SendToExcel('transferlimiter', '', 'all'); 

if (string(Output\[0\]) \<\> '') then 

StatusBar1.Panels\[1\].Text := 'Error: ' + string(Output\[0\]) 

else 

StatusBar1.Panels\[1\].Text := 'ATC calculations done.'; 

end; 

end; 

end; 

end; 

end;

---

<a id="listofdevices-sample-code-matlab"></a>

## ListOfDevices Sample Code Matlab

*Source: [`Content/MainDocumentation_HTML/ListOfDevices_Sample_Code_Matlab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ListOfDevices_Sample_Code_Matlab.htm)*

Sample Code

%A list of branches is desired, without using any filter

DeviceType = 'Branch';

FilterName = '';

%Execute the ListOfDevices command

Output = SimAuto.ListOfDevices(DeviceType,FilterName);

%If the first cell in SimAutoOutput \~= '', then that means an error

%occurred.

if \~(strcmp(SimAutoOutput{1},''))

disp(SimAutoOutput{1}) 

else

%Otherwise, no errors. Display the branch information. 

disp('ListOfDevices successful') 

%Devicelist1 contains the From: bus number 

%Devicelist2 contains the To: bus number 

%Devicelist3 contains the Bus identifier 

devicelist1 = double(transpose(SimAutoOutput{2}{1})); 

devicelist2 = double(transpose(SimAutoOutput{2}{2})); 

devicelist3 = SimAutoOutput{2}{3}; 

%If the device list is greater than 25, don't bother attempting to 

%display it on the screen. 

if (size(devicelist1,1) \> 25)  

disp('Device list exceeds 25; use ''devicelist'' to manage list of devices') 

else  

%Otherwise, display the branches' information. 

disp(DeviceType) 

disp('From/To/Identifier') 

for counter = 1:size(devicelist1,1) 

%num2str converts the numbers within devicelist1 and 

%devicelist2 to strings for output with disp(). the char() 

%function is called on devicelist3's members because the 

%SimAuto object returns a character array (as opposed to a 

%properly Matlab-format string) and this array must be 

%converted to a Matlab-format string. 

disp(\[num2str(devicelist1(counter)) ' ' ... 

num2str(devicelist2(counter)) ' ' ... 

char(devicelist3(counter))\])  

end 

end 

end

---

<a id="listofdevices-sample-code-vb"></a>

## ListOfDevices Sample Code VB

*Source: [`Content/MainDocumentation_HTML/ListOfDevices_Sample_Code_VB.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ListOfDevices_Sample_Code_VB.htm)*

Sample Code

Private Sub DisplayMessage(ByVal SentText As String)

TextBox.Text = TextBox.Text + SentText + vbCrLf + vbCrLf 

End Sub

Private Sub btnListOfDevices\_Click()

Dim objtype, filter As String

Dim xlWB As Excel.Workbook

Set xlApp = Excel.Application

' Checks connection and open case

' SimAuto and caseopen are global variables

If Not SimAuto Is Nothing And caseopen Then

objtype = "branch" 

filter = "" 

output = SimAuto.ListOfDevices(objtype, filter) 

If output(0) \<\> "" Then 

DisplayMessage output(0) 

Else 

DisplayMessage "Succesful List Of Devices" 

' Prepares additional worksheet 

Set xlWB = xlApp.Workbooks.Add 

' Copies list of devices in worksheet 

With xlWB 

Sheets("sheet1").Activate 

Sheets("sheet1").Name = "ListOfDevices" 

With Sheets("ListOfDevices") 

Dim i, j As Integer 

Range(Cells(1, 5), Cells(200, 7)).Clear 

Cells(1, 1) = "List of Devices for " + objtype + ":" 

Cells(2, 1) = "From Bus Num" 

Cells(2, 2) = "To Bus Num" 

Cells(2, 3) = "ID" 

' Determine number of key fields retrieved 

Dim lowkeyf, highkeyf As Integer 

lowkeyf = LBound(output(1), 1) 

highkeyf = UBound(output(1), 1) 

DisplayMessage "Number of Key Fields: " + Str(lowkeyf) + Str(highkeyf) 

' Determine number of objects retrieved 

Dim lowobj, highobj As Integer 

lowobj = LBound(output(1)(lowkeyf), 1) 

highobj = UBound(output(1)(lowkeyf), 1) 

DisplayMessage "Number of objects: " + Str(lowobj) + Str(highobj) 

For i = lowkeyf To highkeyf 

For j = lowobj To highobj 

Cells(j + 3, i + 1) = output(1)(i)(j) 

Next j 

Next i 

End With 

End With 

End If 

End If

End Sub

---

<a id="listofdevicesasvariantstrings"></a>

## ListOfDevicesAsVariantStrings

*Source: [`Content/MainDocumentation_HTML/ListOfDevicesAsVariantStrings_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ListOfDevicesAsVariantStrings_Function.htm)*

This function operates the same as the [ListOfDevices](#listofdevices) function, only with one notable difference. The values returned as the output of the function are returned as Variants of type String. The ListOfDevices function was errantly released returning the values strongly typed as Integers and Strings directly, whereas all other SimAuto functions returned data as Variants of type String. This function was added to also return the data in the same manner. This solved some compatibility issues with some software languages.

---

<a id="listofdevicesflatoutput"></a>

## ListOfDevicesFlatOutput

*Source: [`Content/MainDocumentation_HTML/ListOfDevicesFlatOutput_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ListOfDevicesFlatOutput_Function.htm)*

This function operates the same as the [ListOfDevices](#listofdevices) function, only with one notable difference. The values returned as the output of the function are returned in a single-dimensional vector array, instead of the multi-dimensional array as described in the ListOfDevices topic. The function returns the key field values for the device, typically in the order of bus number 1, bus number 2 (where applicable), and circuit identifier (where applicable). These are the most common key fields, but some object types do have other key fields as well.

The format of the output array is the following:

\[errorString, NumberOfObjectsReturned, NumberOfFieldsPerObject, Ob1Fld1, Ob1Fld2, …, Ob(n)Fld(m-1), Ob(n)Fld(m)\]

The data is thus returned in a single dimension array, where the parameters NumberOfObjectsReturned and NumberOfFieldsPerObject tell you how the rest of the array is populated. Following the NumberOfObjectsReturned parameter is the start of the data. The data is listed as all fields for object 1, then all fields for object 2, and so on. You can parse the array using the NumberOf… parameters for objects and fields.

---

<a id="loadstate"></a>

## LoadState

*Source: [`Content/MainDocumentation_HTML/LoadState_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/LoadState_Function.htm)*

LoadState is used to load the system state previously saved with the [SaveState](#savestate) function. Note that LoadState will not properly function if the system topology has changed due to the addition or removal of the system elements.

Function Prototype

**LoadState()**

Parameter Definitions

No parameters are passed.

Output

LoadState returns only one element in Output—any errors which may have occurred when attempting to execute the function.

---

<a id="loadstate-sample-code"></a>

## LoadState Sample Code

*Source: [`Content/MainDocumentation_HTML/LoadState_Sample_Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/LoadState_Sample_Code.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Microsoft® Visual Basic for Applications

' Make the LoadState call

Output = SimAuto.LoadState()

Matlab®

% Make the LoadState call

Output = SimAuto.LoadState();

---

<a id="opencase"></a>

## OpenCase

*Source: [`Content/MainDocumentation_HTML/OpenCase_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OpenCase_Function.htm)*

The OpenCase function will load a PowerWorldâ Simulator load flow file into the [Simulator Automation Server](33-simauto-overview-and-setup.md#automation-server). This is equivalent to opening a file using the **File \> Open Case** menu option in Simulator.

Function Prototype

**OpenCase(FileName)**

Parameter Definitions

**FileName : String **The name of the PowerWorldâ Simulator case file to be loaded into the Simulator Automation Server. This string includes the directory location and full file name.

Output

OpenCase returns only one element in Output—if the file cannot be found or an error occurs while reading the file.

---

<a id="opencase-sample-code"></a>

## OpenCase Sample Code

*Source: [`Content/MainDocumentation_HTML/OpenCase_Sample_Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OpenCase_Sample_Code.htm)*

Borland® Delphi

Output := SimAuto.OpenCase('c:\\simauto\\examples\\b7opf.pwb');

if (string(Output\[0\]) \<\> '') then

StatusBar1.Panels\[1\].Text := 'Error: ' + string(Output\[0\]); 

else

begin

StatusBar1.Panels\[1\].Text := 'Open Case successful.'; 

// Perform activities with opened case 

end;

Microsoft® Visual Basic for Applications

Output = SimAuto.OpenCase("c:\\simauto\\examples\\b7opf.pwb")

If output(0) \<\> "" Then

MsgBox(output(0)) 

Else

' Perform activities with the opened case 

End If

Matlab®

Output = SimAuto.OpenCase('c:\\simauto\\examples\\b7opf.pwb')

%If the first cell in Output \~= '', then that means an error

%occurred.

if \~(strcmp(Output{1},''))

disp(Output{1}) 

else

%Otherwise, no errors. Perform activities. 

disp('Open Case successful') 

end

---

<a id="opencasetype"></a>

## OpenCaseType

*Source: [`Content/MainDocumentation_HTML/OpenCaseType_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OpenCaseType_Function.htm)*

The OpenCaseType function will load a PowerWorldâ Simulator load flow file into the [Simulator Automation Server](33-simauto-overview-and-setup.md#automation-server). This is similar to opening a file using the **File \> Open Case** menu option in Simulator.

Function Prototype

**OpenCaseType(FileName, FileType, Options)**

Parameter Definitions

**FileName : String **The name of the case file to be loaded into the Simulator Automation Server. This string includes the directory location and full file name.

**FileType : String **The type of case file to be loaded. It can be one of the following strings: PWB, PTI, PTI23,..., PTI35, GE, GE14,..., GE23, CF, AUX, UCTE, AREVAHDB

**Options : Variant** Optional parameter indicating special load options for PTI and GE file types. If specified it should be an array of strings for the specified parameters or a single string if only the first parameter is specified.

**PTI RAW Format Options**

**LoadTransactions**

YES - load transactions when opening case

NO - do not load transactions when opening case

DEFAULT - follow default behavior

**StarBus**

NEAR - star buses are numbered starting after the near bus number

MAX - star buses are numbered starting with the maximum bus number

VALUE - star bus numbering will start at value

**GE EPC Format Options**

**MSLine**

MAINTAIN - maintain multi-section lines

EQUIVALENCE - equivalence multi-section lines

**VarLimDead**

Number - this is the var limit deadband

**PostCTGAGC**

YES - populate the generator field Post-CTG Prevent Response based on the EPC file's generator base load flag

Output

OpenCaseType returns only one element in Output—if the file cannot be found or an error occurs while reading the file.

---

<a id="processauxfile"></a>

## ProcessAuxFile

*Source: [`Content/MainDocumentation_HTML/ProcessAuxFile_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ProcessAuxFile_Function.htm)*

The ProcessAuxFile function will load a PowerWorldâ Auxiliary file into the [Simulator Automation Server](33-simauto-overview-and-setup.md#automation-server). This allows you to create a text file (conforming to the PowerWorldâ Auxiliary file format) that can list a set of data changes and other information for making batch changes in Simulator

Function Prototype

**ProcessAuxFile(FileName)**

Parameter Definitions

**FileName : String **The name of the PowerWorldâ Auxiliary file to be loaded into the Simulator Automation Server. This string includes the directory location and full file name.

Output

ProcessAuxFile returns only one element in Output—any errors which may have occurred when attempting to load the file.

---

<a id="processauxfile-sample-code"></a>

## ProcessAuxFile Sample Code

*Source: [`Content/MainDocumentation_HTML/ProcessAuxFile_Sample_Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ProcessAuxFile_Sample_Code.htm)*

Microsoft® Visual Basic for Applications

Dim filename As String

' Setup name of aux file to run

filename = "c:\\auxdirectory\\b7opf\_ctglist.aux"

' Make the processAuxFile call

Output = SimAuto.ProcessAuxFile(filename)

Matlab®

% Setup name of aux file to run

filename = 'c:\\auxdirectory\\b7opf\_ctglist.aux';

% Make the processAuxFile call

Output = SimAuto.ProcessAuxFile(filename);

---

<a id="runscriptcommand"></a>

## RunScriptCommand

*Source: [`Content/MainDocumentation_HTML/RunScriptCommand_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/RunScriptCommand_Function.htm)*

The RunScriptCommand function is used to execute a list of script statements. The script actions are those included in the script sections of the [Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux). If an error occurs trying to run a script command, an error will be returned through EString.

Function Prototype

**RunScriptCommand(Statements)**

Parameter Definitions

**Statements : String **The block of script actions to be executed. Each script statement must end in a semicolon. The block of script actions should **not** be enclosed in curly braces.

Output

RunScriptCommand returns only one element in Output—any errors which may have occurred when attempting to load or run the auxiliary file.

---

<a id="runscriptcommand-sample-code"></a>

## RunScriptCommand Sample Code

*Source: [`Content/MainDocumentation_HTML/RunScriptCommand_Sample_Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/RunScriptCommand_Sample_Code.htm)*

Microsoft® Visual Basic for Applications

Dim scriptcommand As String

' Set script command to cause Simulator to enter Run Mode

scriptcommand = "EnterMode(RUN)"

' Make the RunScriptCommand call

Output = SimAuto.RunSCriptCommand(scriptcommand);

' Set script command to cause Simulator to perform a single,

' standard solution

scriptcommand = "SolvePowerFlow(RECTNEWT)"

' Make the RunScriptCommand call

Output = SimAuto.RunSCriptCommand(scriptcommand);

Matlab®

% Set script command to cause Simulator to enter Run Mode

scriptcommand = 'EnterMode(RUN)';

% Make the RunScriptCommand call

Output = SimAuto.RunSCriptCommand(scriptcommand);

% Set script command to cause Simulator to perform a single,

% standard solution

scriptcommand = 'SolvePowerFlow(RECTNEWT)';

% Make the RunScriptCommand call

Output = SimAuto.RunSCriptCommand(scriptcommand);

---

<a id="runscriptcommand2"></a>

## RunScriptCommand2

*Source: [`Content/MainDocumentation_HTML/RunScriptCommand2_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/RunScriptCommand2_Function.htm)*

(Added in version 21, build on August 4, 2020)

This function is available starting with the *pwrworld 21.0 type library*.

The RunScriptCommand2 function is used to execute a list of script statements. The script actions are those included in the script sections of the [Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux). This function differs from RunScriptCommand in that it allows informational messages to be returned from the script execution when the execution is successful.

Function Prototype

**RunScriptCommand2(Statements, out StatusMessage)**

Parameter Definitions

**Statements : String **The block of script actions to be executed. Each script statement must end in a semicolon. The block of script actions should **not** be enclosed in curly braces.

**StatusMessage : String **This is an out parameter that returns any informational or error messages resulting during execution of the script command.

Output

**Boolean** result indicating if the script command was successful or not. If *False* is returned, an error message will be returned in **StatusMessage**. **StatusMessage** may be blank if *True* is returned.

---

<a id="savecase"></a>

## SaveCase

*Source: [`Content/MainDocumentation_HTML/SaveCase_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SaveCase_Function.htm)*

The SaveCase function is used to save a case previously loaded in the [Simulator Automation Server](33-simauto-overview-and-setup.md#automation-server) using the [OpenCase](#opencase) function. The function allows you to specify a file name and a format for the save file.

Function Prototype

**SaveCase(FileName, FileType, Overwrite)**

Parameter Definitions

**FileName : String **The name of the file you wish to save as, including file path.

**FileType : String **A string indicating the format of the written case file. An empty string will return an error. The following list is the currently supported list of string identifiers and the file types they represent.

"PTI23" - "PTI35" specific PTI version (raw)  
"GE14" - "GE23" GE PSLF version (epc)  
"IEEE"  IEEE common format (cf)

"UCTE" UCTE Data Exchange (uct)

"AUXNETWORK" PowerWorld Auxiliary format (aux) saving only network data. This is the recommended auxiliary file type.

When saving an auxiliary file, the following file types are supported for compatibility with existing processes that users might have in place, but the recommended option is "AUXNETWORK".

"AUX"  PowerWorld Auxiliary format (aux).

"AUXSECOND" PowerWorld Auxiliary format (aux) using secondary key fields.

"AUXLABEL" PowerWorld Auxiliary format (aux) using labels as key field identifiers.

"PWB5" - "PWB24"  specific PowerWorld Binary version (pwb)  
"PWB"  PowerWorld Binary (most recent) (pwb)

**Overwrite : Boolean **A Boolean value which indicates whether to overwrite a file if FileName already exists. If Overwrite is set to false and the file specified by FileName already exists, SaveCase will return an error message and do nothing to the file.

Output

SaveCase returns only one element in Output—any errors that may have occurred when attempting to save the case.

---

<a id="savecase-sample-code"></a>

## SaveCase Sample Code

*Source: [`Content/MainDocumentation_HTML/SaveCase_Sample_Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SaveCase_Sample_Code.htm)*

Microsoft® Visual Basic for Applications

' Save the case as a PWB file

Output = SimAuto.SaveCase("c:\\casedirectory\\b7opfcopy.pwb", "PWB", true)

' Save the case as a PTI file

Output = SimAuto.SaveCase("c:\\casedirectory\\b7opfcopy.raw", "PTI", true)

Matlab®

% Setup name of PWB file to write

filenamepwb = 'c:\\casedirectory\\b7opfcopy.pwb';

% Setup name of PTI file to write

filenamepti = 'c:\\casedirectory\\b7opfcopy.raw';

% Make the SaveCase call for the PWB file

Output = SimAuto.SaveCase(filenamepwb, ‘PWB’, true);

% Make the SaveCase call for the PTI file

Output = SimAuto.SaveCase(filenamepti, ‘PWB’, true);

---

<a id="savestate"></a>

## SaveState

*Source: [`Content/MainDocumentation_HTML/SaveState_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SaveState_Function.htm)*

SaveState is used to save the current state of the power system. This can be useful if you are interested in comparing various cases, much as the [Difference Flows](08-view-case-data-tools.md#difference-case) feature works in the Simulator application.

Function Prototype

**SaveState()**

Parameter Definitions

No parameters are passed.

Output

SaveState returns only one element in Output—any errors which may have occurred when attempting to execute the function.

---

<a id="savestate-sample-code"></a>

## SaveState Sample Code

*Source: [`Content/MainDocumentation_HTML/SaveState_Sample_Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SaveState_Sample_Code.htm)*

Microsoft® Visual Basic for Applications

' Make the SaveState call

Output = SimAuto.SaveState()

Matlab®

% Make the SaveState call

Output = SimAuto.SaveState();

---

<a id="sendtoexcel"></a>

## SendToExcel

*Source: [`Content/MainDocumentation_HTML/SendToExcel_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SendToExcel_Function.htm)*

The SendToExcel function can be called to send data from the [Simulator Automation Server](33-simauto-overview-and-setup.md#automation-server) to an Excel spreadsheet. The function is flexible in that you can specify the type of object data you want to export, an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) name for a filter you want to use, and as many or as few [field types](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names) as desired that are supported by the type of object. The first time this function is called, a new instance of Excel will be started, and the data requested will be pasted to a new sheet. For each subsequent call of this function, the requested data will be pasted to a new sheet within the same workbook, until the workbook is closed.

Function Prototype

**SendToExcel(ObjectType, FilterName, FieldList)**

Parameter Definitions

**ObjectType : String **A string describing the type of object for which you are requesting data.

**FilterName : String **The name of an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) which was previously defined in the case before being loaded in the Simulator Automation Server. If no filter is desired, then simply pass an empty string. If a filter name is passed but the filter cannot be found in the loaded case, no filter is used.

**FieldList : Variant **This parameter must either be an array of fields for the given object or the string "ALL". As an array, FieldList contains an array of strings, where each string represents an object field variable, as defined in the section on [PowerWorld Object Variables](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names). If, instead of an array of strings, the single string "ALL" is passed, the Simulator Automation Server will use predefined default fields when exporting the data.

Output

SendToExcel returns only one element in Output—any errors which may have occurred when attempting to execute the function.

---

<a id="sendtoexcel-sample-code"></a>

## SendToExcel Sample Code

*Source: [`Content/MainDocumentation_HTML/SendToExcel_Sample_Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SendToExcel_Sample_Code.htm)*

Microsoft® Visual Basic for Applications

Dim FieldList As Variant

' Setup fieldlist to send the bus number, gen id and gen agc to Excel

FieldList = Array("BusNum", "GenID", "GenAGCAble")

' Make the SendToExcel call

' By specifying the parameter FieldList, only the three fields

' for each generator will be returned

Output = SimAuto.SendToExcel("gen", "", "FieldList")

' Sending the string "all" instead of a fieldlist array

' writes all predefined fields to the Excel spreadsheet

Output = SimAuto.SendToExcel("gen", "", "all")

Note:  This function call will send the values of the fields in FieldList to an Excel workbook for all the generators in the load flow case. If a filter name had been passed instead of an empty string, Simulator would have located and used a pre-defined advanced filter and applied it to the information if it was found.

Matlab®

% Setup fieldlist to send the bus number, gen id and gen agc to Excel

fieldlist = {'BusNum' 'GenID' 'GenAGCAble' };

% Make the SendToExcel call

Output = SimAuto.SendToExcel('gen', '' , FieldList);

% Sending the string 'all' instead of a fieldlist array

% writes all predefined fields to the Excel spreadsheet

Output = SimAuto.SendToExcel('gen', '', 'all');

Note:  This function call will send the values of the fields in FieldList to an Excel workbook for all the generators in the load flow case. If a filter name had been passed instead of an empty string, Simulator would have located and used a pre-defined advanced filter and applied it to the information if it was found.

---

<a id="tsgetcontingencyresults"></a>

## TSGetContingencyResults

*Source: [`Content/MainDocumentation_HTML/TSGetContingencyResults Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TSGetContingencyResults Function.htm)*

TSGetCongencyResults function

The TSGetContingencyResults function is used to read transient stability results into an external program (i.e. Matlab or VB) using SimAuto.

This function is analogous to the script command TSGetResults, where rather than saving out results to a file, the results are passed back directly to the SimAuto COM object and may be further processed by an external program. As with TSGetResults, this function should only be used after the simulation is run (for example, use this after running script commands TSSolveAll or TSSolve).

Function Prototype

**TSGetContingencyResults(CtgName, ObjFieldList, StartTime, StopTime)**

Parameter Definitions

**CtgName : String **The contingency to obtain results from. Only one contingency be obtained at a time.

**ObjFieldList: Variant**A variant array of strings which may contain plots, subplots, or individual object/field pairs specifying the result variables to obtain.

**StartTime : String **The time in seconds in the simulation to begin retrieving results. If not specified, the start time of the simulation is used.

**StopTime : String **The time in seconds in the simulation to stop retrieving results. If not specified, the end time of the simulation is used.

Output

The SimAuto output for this function is a Variant which contains three levels. Output(0) displays an error message, if any. Output(1) displays the header which describes the variables that were saved out. Output(2) displays the time series data (numerical results from simulation), corresponding to the variables described in the header. MATLAB indexing begins at 1 instead of 0, so add one to all the indices shown when using MATLAB.

![TSGetContingencyResultsObjectStructure](images/TSGetContingencyResultsObjectStructure.gif)

---

<a id="tsgetcontingencyresults-sample-code"></a>

## TSGetContingencyResults Sample Code

*Source: [`Content/MainDocumentation_HTML/TSGetContingencyResults Sample Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TSGetContingencyResults Sample Code.htm)*

Sample code (VB):

Set mySimAuto = New pwrworld.SimulatorAuto

Output = mySimAuto.OpenCase("G:\\wscc\_9busCacheTest.pwb")

If Output(0) \<\> "" Then

DisplayErrorMessage Output(0)

End If

Dim objFieldList As Variant

objFieldList = Array("Plot 'Gen\_Rotor Angle'", "Bus 4 | frequency")

Output = mySimAuto.TSGetContingencyResults("ctgname1", objFieldList, "0.0", "10.0")

If Output(0) \<\> "" Then

DisplayErrorMessage Output(0)

End If

Set SimAuto = Nothing

![TSGetContingencyResults VBOutput](images/TSGetContingencyResults_VBOutput.gif)

Sample code (Matlab):

%Initialize SimAuto object

SimAuto = actxserver('pwrworld.SimulatorAuto');

%Initialize SimAutoOutput which is used to store the output of every method call

clear SimAutoOutput;

SimAutoOutput = {''};

%Open the case

SimAutoOutput = SimAuto.OpenCase('G:\\wscc\_9busCacheTest.pwb');

if \~(strcmp(SimAutoOutput{1},''))

disp(SimAutoOutput{1})

else

disp('OpenCase successful')

end

%%

% Here we get the results for all of the angles directly into Matlab via SimAuto

%%

newCtgName = 'ctgName';

objFieldList = {'"Plot ''Gen\_Rotor Angle''"' };

SimAutoOutput = SimAuto.TSGetContingencyResults(newCtgName, objFieldList , '0.0', '10.0');

if \~(strcmp(SimAutoOutput{1},''))

disp(SimAutoOutput{1})

else

disp('GetTSResultsInSimAuto successful')

%Get the results

localResults = SimAutoOutput{3};

%Get the header variables to use for plot labels

Header = SimAutoOutput{2};

% Convert a matrix of strings into a matrix of numbers and plot them

localResultsMat = str2double(localResults);

plot(localResultsMat(:,1), localResultsMat(:,\[2:size(localResultsMat,2)\]));

title(\['Transient stability results for ', newCtgName\]);

TimeSeriesNames = Header(\[4:size(Header,1)\],2);

legend(TimeSeriesNames); % these labels come from the HEADER

xlabel('time')

ylabel('Generator rotor angle (degrees)');

end

%Delete (close) the COM object.

delete(SimAuto);

![TSGetContingencyResults MatLabOutput1](images/TSGetContingencyResults_MatLabOutput1.gif)

![TSGetContingencyResults MatlabOutput2](images/TSGetContingencyResults_MatlabOutput2.gif)

---

<a id="writeauxfile"></a>

## WriteAuxFile

*Source: [`Content/MainDocumentation_HTML/WriteAuxFile_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/WriteAuxFile_Function.htm)*

The WriteAuxFile function can be used to write data from the case in the [Simulator Automation Server](33-simauto-overview-and-setup.md#automation-server) to a PowerWorldâ Auxiliary file. The function is flexible in that you can specify the type of object data you want to export, an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) name for a filter you want to use, and as many or as few field types as desired that are supported by the type of object. In addition, you can specify a new file name for each call to WriteAuxFile, or you can specify the same file name and append the data to the file.

Function Prototype

**WriteAuxFile(FileName, FilterName, ObjectType, ToAppend, FieldList)**

Parameter Definitions

**FileName : String **The name of the PowerWorldâ Auxiliary file you wish to save.

**FilterName : String **The name of an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) which was previously defined in the case before being loaded in the Simulator Automation Server. If no filter is desired, then simply pass an empty string. If a filter name is passed but the filter cannot be found in the loaded case, no filter is used.

**ObjectType : String **A string describing the type of object for which your are requesting data.

**ToAppend : Boolean **If you have given a file name of an auxiliary file that already exists, the file will either be appended to or overwritten according to the setting of this parameter. *False* means to overwrite an existing file and *True* means to append to an existing file.

**FieldList : Variant **This parameter must either be an array of fields for the given object or the string "ALL". As an array, FieldList contains an array of strings, where each string represents an object field variable, as defined in the section on [PowerWorld Object Variables](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names). If, instead of an array of strings, the single string "ALL" is passed, all fields for the objecttype will be included when exporting the data.

Output

WriteAuxFile returns only one element in Output—any errors which may have occurred when attempting to execute the function.

---

<a id="writeauxfile-sample-code"></a>

## WriteAuxFile Sample Code

*Source: [`Content/MainDocumentation_HTML/WriteAuxFile_Sample_Code.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/WriteAuxFile_Sample_Code.htm)*

Microsoft® Visual Basic for Applications

Dim FieldList As Variant

Dim auxfilename As String

' Setup FieldList to send the bus number, gen id and gen agc

FieldList = Array("BusNum", "GenID", "GenAGCAble")

' Aux file to write to

auxfilename = "c:\\auxiliarydirectory\\businfo.aux"

' Make the WriteAuxFile call

' By specifying the parameter FieldList, only the three fields

' for each generator will be returned

Output = SimAuto.WriteAuxFile(auxfilename, "", "gen", true, FieldList)

' Sending the string "all" instead of the FieldList array

' writes all predefined fields to the Excel spreadsheet

Output = SimAuto.SendToExcel(auxfilename, "", "gen", true, "all")

Note:  This function call will send the values of the fields in FieldList to an auxiliary file for all the generators in the load flow case. If a filter name had been passed instead of an empty string, Simulator would have located and used a pre-defined advanced filter and applied it to the information if it was found.

Matlab®

% Setup FieldList to send the bus number, gen id and gen agc

fieldlist = {'BusNum' 'GenID' 'GenAGCAble' };

% Aux file to write to

auxfilename = 'c:\\auxiliarydirectory\\businfo.aux';

% Make the WriteAuxFile call

Output = SimAuto.WriteAuxFile(auxfilename, '', 'gen', true, FieldList);

% Sending the string 'all' instead of the FieldList array

% writes all predefined fields to the .aux file

Output = SimAuto.WriteAuxFile(auxfilename, '', 'gen', true, 'all');

Note:  This function call will send the values of the fields in FieldList to an auxiliary file for all the generators in the load flow case. If a filter name had been passed instead of an empty string, Simulator would have located and used a pre-defined advanced filter and applied it to the information if it was found.
