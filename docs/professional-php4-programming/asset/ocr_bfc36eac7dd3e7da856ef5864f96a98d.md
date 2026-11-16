```
```xml
<tr>
<td>
<xsl:text>Resort_typeofholiday</xsl:text>
</td>
<td>
<xsl:value-of select="Resort_watersports" />
</td>
</tr>
<tr>
<td>
<xsl:text>Resort_watersports</xsl:text>
</td>
<td>
<xsl:value-of select="Resort_watersports" />
</td>
</tr>
<tr>
<td>
<xsl:text>Resort_meals</xsl:text>
</td>
<td>
<xsl:value-of select="Resort_meals" />
</td>
</tr>
<tr>
<td>
<xsl:text>Resort_drinks</xsl:text>
</td>
<td>
<xsl:value-of select="Resort_drinks" />
</td>
</tr>
<tr>
<td>
<xsl:text>Package_dateofdep</xsl:text>
</td>
<td>
<xsl:value-of select="*/Package_dateofdep" />
</td>
</tr>
<tr>
<td>
<xsl:text>Package_price</xsl:text>
</td>
<td>
<xsl:value-of select="*/Package_price" />
</td>
</tr>
<tr>
<td colspan="2"><hr /></td>
</tr>
</xsl:for-each>
</table>
</body>
</html>
</xsl:template>
</xsl:stylesheet>
```
```