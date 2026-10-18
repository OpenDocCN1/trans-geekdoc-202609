# FIGURE 3.3 How nested ordered and unordered lists appear in a browser

![](bbox=[0.1, 0.08, 0.8, 0.32])

# Definition lists

Definition lists are a bit different from the other types of list because they are structured as a glossary of terms. The outer element of a definition list uses the <DL> . . . </DL> (definition list) tags. Inside this element appear one or more pairs of terms and definitions. In each pair, the term is defined by a DT (definition term) element and the definition appears in a DD (definition list definition) element. Here is an example of an HTML document containing a definition list:

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org/TR/html4/strict.dtd">
<HTML>
    <HEAD>
        <TITLE>Markup Languages</TITLE>
    </HEAD>
    <!-- File: example3-4.htm -->
<BODY>
    <DL>
        <DT> SGML </DT>
        <DD> Standard Generalised Markup Language </DD>
        <DT> HTML </DT>
        <DD> HyperText Markup Language </DD>
        <DT> XML</DT>
        <DD> eXtensible Markup Language </DD>
    </DL>
</BODY>
</HTML>
```

Figure 3.4 shows how the definition list looks in Mozilla Firefox 2. In this browser, there is no difference in the font size or style between the definitions and the terms, only the layout is affected. We could, however, add EM or STRONG tags to provide some further semantic differentiation between definitions and terms.