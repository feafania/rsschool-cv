# Tatsiana Kashko
## Contacts:
* **E-mail**: *t.kashko@gmail.com*
* **discord**: *feafania*
* **GitHub**: [*feafania*](https://github.com/feafania)

## Profile:
<img src="./Profile.jpg" alt="My picture" width="126" height="126">

I solve problems of various scopes and levels and have the skills of both a programmer and a business analyst. I can independently explore the field of automation and build the logic of production and business processes.

## Skills:
* 1с-language
* VB-Script and VBA
* html, xml
* Wordpress
* VS-Code

## Professional Experience:
* Automation of business from scratch: **JSC Skidel Sugar Refinery, PT LLC Taifun Hrodna, J LLC ZOV-Lenevromebel**. 
* Administration of Windows domains, Active Directory. 
* Teaching at Institute of Postgraduate Education at Hrodna State University: 
	* Data structures;
	* Economic and mathematical methods and models;
	* Automated business systems.

## Education:
* Yanka Kupala Hrodna State University, specialty **"Economic Cybernetics"**, specialization "Software engineering and technologies";
* Postgraduate course of Belarusian State University **"Mathematical Cybernetics"**;
* Institute of Postgraduate Education at Hrodna State University, specialty **"English language teacher"**.

## Languages:
* Belarusian (native);
* English (B2, I've been living in the UK for 7 months);
* Polish (B2).

## Code Examples:
* [The first project in RS School](https://github.com/feafania/rsschool-cv/tree/gh-pages)

* **Procedures 1c**:
```1c
// ConvertCharset(InputFile, OutputFile, InitialEncoding = "utf-8", FinalEncoding = "windows-1251")
//
// Options:
//  InputFile - original file
//  OutputFile - resulting file
//  InitialEncoding - Initial Encoding
//  FinalEncoding - Final Encoding
//
// Description:
//	Converts a file from one encoding to another
//
Procedure ConvertCharset(InputFile, OutputFile, InitialEncoding = "utf-8", FinalEncoding = "windows-1251") Export
	ObjOleExSupCreated = 0;
	Try
		OleExSup = CreateObject("OleExSup");
		ObjOleExSupCreated = 1;
	Except
		If LoadExternalComponent(IBDir()+"ExtForms\OleExSup.dll")=0 Then
			If LoadExternalComponent("OleExSup.dll")=1 Then
				ObjOleExSupCreated = 1;
			EndIf;   
		Else
			ObjOleExSupCreated = 1;
		EndIf;    
		If ObjOleExSupCreated = 1 Then
			OleExSup = CreateObject("OleExSup"); 
		EndIf;
	EndTry;

	// Read the content from the input file with initial encoding
	InputStream = CreateObject("ADODB.Stream");
	InputStream.Open();
	InputStream.Charset = InitialEncoding;
	InputStream.LoadFromFile(InputFile);
	
	// Write the content to the output file with final encoding    
	Try
		OutputStream = CreateObject("ADODB.Stream");
		OutputStream.Open();
		OutputStream.Charset = FinalEncoding;
		If ObjOleExSupCreated = 1 Then    
			OleExSup.InvokeOLEMethod(OutputStream, "WriteText", InputStream.ReadText());
			OleExSup.InvokeOLEMethod(OutputStream, "SaveToFile", OutputFile, 2);
		Else
			OutputStream.WriteText(InputStream.ReadText());
			OutputStream.SaveToFile(OutputFile, 2); // 2 for overwrite
			OutputStream.Close();
		EndIf;
	Except   
		Message(GetErrorDescription());
	EndTry;
	InputStream.Close();
	
EndProcedure // ConvertCharset()   
```
