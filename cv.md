# Tatsiana Kashko

## Contacts
* **E-mail**: t.kashko@gmail.com
* **GitHub**: [feafania](https://github.com/feafania)
* **Discord**: feafania

## Summary
A specialist with strong analytical and programming skills, able to handle tasks of varying complexity. Experienced in researching automation domains and designing logical structures for production and business processes.

[//]: # (![My picture]&#40;./assets/img/avatar.jpg&#41;)

## Skills
* **Frontend**: JavaScript, TypeScript, HTML, CSS, Figma
* **Backend**: Node.js, Express
* **Databases**: MS SQL, MongoDB
* **Tools**: GitHub, VS Code, WebStorm

## Professional Experience
* Designed and implemented end-to-end business automation systems
* Managed Windows domain infrastructures and Active Directory services
* Delivered academic courses at the Institute of Postgraduate Education (Hrodna State University):
	* Data Structures
	* Economic & Mathematical Models
	* Business Automation Systems

## Projects
* JSC Skidel Sugar Refinery – automation of accounting
* PT LLC Taifun Hrodna – full-cycle automation
* J LLC ZOV-Lenevromebel – automation of accounting and business processes

### RS School Projects
* [RS School: Shelter](https://feafania.github.io/RSSchool/shelter/)
* [RS School: Christmas Shop](https://feafania.github.io/RSSchool/christmas-shop/)
* [RS School: Async Race](https://github.com/feafania/RSSchool/tree/async-race)
* [RS School: Hangman](https://github.com/feafania/RSSchool/tree/hangman)
* [RS School: News API](https://github.com/feafania/RSSchool/tree/news-api)

### Additional GitHub Projects
* [CommerceTools: Product & Cart Service](https://github.com/feafania/CommerceTools)
* [IT-Incubator: Backend Course Projects](https://github.com/feafania/Incubator)

## Education
* Yanka Kupala State University of Hrodna — **Economic Cybernetics** (specialization: Software Engineering & Technologies)
* Belarusian State University — Postgraduate Studies in **Mathematical Cybernetics**
* Institute of Postgraduate Education — **English Language Teaching Qualification**

## Courses
* The Rolling Scopes School — JS/FE Pre-School 2024Q2 (JavaScript)
* The Rolling Scopes School — JS/FE EN 2024Q4 (JavaScript)
* IT-Incubator — Backend (in progress)

## Languages
* Belarusian (native)
* English (B2)
* Polish (B2)

## Code Examples

### JavaScript
```javascript
function rgb(r, g, b) {
    function formattedString(b) {
        if (b.length === 1) {return `0${b.toUpperCase()}`}
        else {return b.toUpperCase()};
    }
    function roundNumber(b) {
      return Math.min(Math.max(b,0),255)
    }
    return `${formattedString(roundNumber(r).toString(16))}${formattedString(roundNumber(g).toString(16))}${formattedString(roundNumber(b).toString(16))}`;
}
```

### Procedures 1c
```1c
// ConvertCharset(InputFile, OutputFile, InitialEncoding = "utf-8", FinalEncoding = "windows-1251")
//
// Options:
//  InputFile - original file
//  OutputFile - resulting file
//  InitialEncoding - initial Encoding
//  FinalEncoding - final Encoding
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
