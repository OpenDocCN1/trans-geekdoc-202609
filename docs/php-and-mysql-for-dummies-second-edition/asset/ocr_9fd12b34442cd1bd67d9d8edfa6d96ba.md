# Listing 12-3 (continued)

```
<tr><td align="right"><b>City</b></td>
    <td><input type="text" name="city"
        value="<?php echo @$city ?>"
        size="40" maxlength="40"></td></tr>
<tr><td align="right"><b>State</b></td>
    <td><select name="state">
<?php
    $stateName=getStateName();          #86
    $stateCode=getStateCode();          #87
    for ($n=1;$n<=50;$n++)
    {
        $state=$stateName[$n];
        $scode=$stateCode[$n];
        echo "<option value=\"$scode\"";
        if ($scode=="AL")
            echo " selected";
        echo ">$state\n";
    }
?>
    </select>
    &nbsp;&nbsp;&nbsp;&nbsp;<b>Zip</b>
    <input type="text" name="zip"
        value="<?php echo @$zip ?>"
        size="10" maxsize="10">
</td></tr>
<tr><td align=right><b>Phone</b></td>
    <td><input type="test" name="phone"
        value="<?php echo @$phone ?>"
        size="15" maxlength="20">
    &nbsp;&nbsp;&nbsp;<b>Fax</b>
    <input type="text" name="fax"
        value="<?php echo @$fax ?>"
        size="15" maxlength="20"></td></tr>
<tr><td align=right><b>Email Address</b></td>
    <td><input type="test" name="email"
        value="<?php echo @$email ?>"
        size="55" maxlength="67"></td></tr>
<tr><td>&nbsp;</td>
    <td align="center">
        <input type="submit"
            value="Become a Member"></td>
</tr>
</table>
</form>
</td>
</tr>
<tr><td colspan="3" bgcolor="gray">&nbsp;</td></tr>
</table>
```