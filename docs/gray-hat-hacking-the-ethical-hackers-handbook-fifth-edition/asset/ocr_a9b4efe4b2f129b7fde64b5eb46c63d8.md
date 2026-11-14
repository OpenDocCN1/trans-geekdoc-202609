```
BOOL ResolveCryptAPIs()
{
    BOOL result;
    HMODULE rLoadLibrary;
    HMODULE v2;
    BOOL ( __stdcall *CryptGenKey_)(HCRYPTPROV, ALG_ID, DWORD, HCRYPTKEY *);
    if ( CryptAcquireContextA )
        return 1;
    rLoadLibrary = LoadLibraryA(LibFileName);
    v2 = rLoadLibrary;
    result = 0;
    if ( rLoadLibrary )
    {
        CryptAcquireContextA = GetProcAddress(rLoadLibrary, aCryptacquireco);
        CryptImportKey = GetProcAddress(v2, aCryptimportkey);
        CryptDestroyKey = GetProcAddress(v2, aCryptdestroyke);
        CryptEncrypt = GetProcAddress(v2, aCryptencrypt);
        CryptDecrypt = GetProcAddress(v2, aCryptdecrypt);
        CryptGenKey_ = GetProcAddress(v2, aCryptgenkey);
        CryptGenKey = CryptGenKey_;
        if ( CryptAcquireContextA )
        {
            if ( CryptImportKey && CryptDestroyKey && CryptEncrypt &&
                CryptDecrypt && CryptGenKey_ )
                result = 1;
        }
    }
    return result;
}
```

![](bbox=[0.13, 0.63, 0.25, 0.71])

NOTE Dynamic resolution of API functions using LoadLibrary and GetProcAddress is a common occurrence in malware. It allows the authors to hide the functionality from the static analysis tools relying on the import table. Another improvement on this approach is obfuscating or encrypting the strings of API functions, which further prevents static signatures and reasoning about executable functionality. When analyzing malware, make sure you check LoadLibrary and GetProcess API references in code and determine if they are resolving additional APIs.

When dealing with dynamically resolved APIs in IDA, you can name the variables as the resolved functions, and IDA will automatically apply the corresponding API prototype.