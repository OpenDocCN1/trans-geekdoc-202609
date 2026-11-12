| | Source text with formatting tags | Target text in Chinese with formatting tags |
|---|---|---|
| Website content to be localized | This word is displayed in bold | 这是个黑体字 |
| HTML | <p> This word is displayed in <b>bold</b></p> | <p>这是个<b>黑体</b><字></p> |
| XLIF | <source>
This word is displayed in
<g id="1"> 
<btype="bold">&lt;b&gt;&gt;/&lt;/g&gt;
bold
<g id="1">"&lt;/b&gt;&gt;/<g>
</source> | <target>
这是个
<g id="1"> 
<ctype="bold">&lt;lt;&b&gt;&gt;/<g>
黑体
<g id="1">"&lt;/lt;&b&gt;&gt;/<g>
字
</target> |
| Tag movement | This word is displayed in <l> bold </l> | 这是个 <l> 黑体 </l>字 |

FIGURE 7.2 Projecting source tags into the translated text

correct position, human post-editors must manually correct them in the post-
editing process.

Figure 7.2 shows an example of data exchange in HTML, XLIF, and tag format in an MT system. As shown in the figure, the word *bold* is bolded, which is marked by <b> and </b> in HTML and <g id="1"> in XLIF. The bold tag is on the last word in the source text, yet in Chinese, the correct tag position should be one character (字, meaning ‘character’) before the last word. This is due to differences in linguistic structures between English and Chinese. Ideally an MT system can capture this difference. Otherwise, a translator or post-editor needs to manually correct it.

Editing such inline tags in MT is a specialized annotation task, and the translator requires some basic knowledge of the XML markup language to edit accurately. Project managers can provide training to editors to help them understand the meaning of the inline tags. As XML is an extensible markup language, program developers can customize the markup language schema, which makes the meaning of these tags dynamic in different systems. For example, <l> may mean bold font in one project but italicized font in another. The translator requires this type of information to perform the tag editing tasks.

# 7.5 TCI by using language data

In addition to the human element being embedded in the design and compilation of language data and the data annotation process, significant subjective human intervention comes into play when a user analyzes or uses the language data. Generally