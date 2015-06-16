//------------------------------------------------------------------
//  MONIgnse.bdh 
//  Generates Name, Surname, Email
//  To generate unique name use GenFName_gnse, for surname use GenSName_gnse
//  and for email use GenEmail.
//------------------------------------------------------------------

dclrand
    sIn_gnse           : RndStr(1..1);
    sBody_gnse         : RndStr(5..12);
    sEmailDel_gnse     : RndStr(".-_", 1..1);
    sEmailId_gnse      : RndStr("1234567890", 0..4);
    sCompanyName_gnse  : RndStr(3..10);
    nDomainSelect_gnse : RndUniN(1..9);


//***function: generate first name
dclfunc
  function GenFName_gnse(sFirstName_gnse : string):string

  begin
    sFirstName_gnse := sIn_gnse + Strlwr(sBody_gnse);
  end GenFName_gnse;


//***function: generate surname 
dclfunc
  function GenSName_gnse(sSecondName_gnse : string):string

  begin
    sSecondName_gnse := sIn_gnse + Strlwr(sBody_gnse);
  end GenSName_gnse;


//***function: generate name, surname, email 
dclfunc
  function GenEmail_gnse(sEmail_gnse : string; sFirstName_gnse : string; sSecondname_gnse : string ):string
  var
    sDomainName_gnse  : string;
    sFirstNameL_gnse  : string; //for lowercase 
    sSecondnameL_gnse : string; //for lowercase
    //nDomainSelect_gnse upper limit must be the same as number of list elements 
    listDomains_gnse  : list of string init "com", "co.uk", "co", "io", "lon", "net", "org", "gov", "edu";
      
  begin
    GenFName_gnse(sFirstName_gnse);
    GenSName_gnse(sSecondname_gnse);
    
    sFirstNameL_gnse  := sFirstName_gnse;
    sSecondnameL_gnse := sSecondname_gnse;
    
    ListGetAt(listDomains_gnse,nDomainSelect_gnse,sDomainName_gnse);
    
    sEmail_gnse := Strlwr(sFirstNameL_gnse) + sEmailDel_gnse + Strlwr(sSecondnameL_gnse) + sEmailId_gnse + "@" + Strlwr(sCompanyName_gnse) + "." + sDomainName_gnse;
  end GenEmail_gnse;
  
  
//***function: generate email by MSISDN 
dclfunc
  function GenEmailMSISDN_gnse(sEmail_gnse : string; sMSISDN_gnse : string):string
  var
    sDomainName_gnse  : string;
    //nDomainSelect_gnse upper limit must be the same as number of list elements 
    listDomains_gnse : list of string init "com", "co.uk", "co", "io", "lon", "net", "org", "gov", "edu";
     
  begin
    
    ListGetAt(listDomains_gnse,nDomainSelect_gnse,sDomainName_gnse);
    
    sEmail_gnse := sMSISDN_gnse + "@" + Strlwr(sCompanyName_gnse) + "." + sDomainName_gnse;
  
  end GenEmailMSISDN_gnse;
  
//***function: convert word to camelcase
dclfunc 
  function toCamelCase(sWord : string): string
  var 
    i, len      : number;
    sPart       : string;
    sResult     : string;
   
  begin
    len := Strlen(sWord);
    i   := len;
    while i > 0 do
      //extract individual character
      Strncpy(sPart, sWord, i);
      sPart := Strrev(sPart);
      Strncpy(sPart, sPart, 1);
      
      //character to uppercase 
      if (i mod 2 = 1) then
        sPart := Strupr(sPart);
      end;
      
      //generates result string
      sResult := sResult + sPart;
      i := i - 1;
    end;
    toCamelCase := Strrev(sResult); //return result
    
   end toCamelCase;
