# Core PHP Programming

![](bbox=[0.231, 0.096, 0.558, 0.467])

print("<B>Using settype</B><BR>\n");
$AverageTemperature = "60.5 degrees";
print("String: \$AverageTemperature <BR>\n");

settype($AverageTemperature, "double");
print("Double: \$AverageTemperature <BR>\n");

settype($AverageTemperature, "integer");
print("Integer: \$AverageTemperature <BR>\n");

settype($AverageTemperature, "string");
print("String: \$AverageTemperature <BR>\n");

print("<B>Using strval, intval</B><BR>\n");
print("and doubleval</BR><BR>\n");
$AverageTemperature = "60.5 degrees";

print("String: ");
print("strval(\$AverageTemperature));
print("<BR>\n");

print("Double: ");
print("doubleval(\$AverageTemperature));
print("<BR>\n");

print("Integer: ");
print("intval(\$AverageTemperature));
print("<BR>\n");

print("Original: ");
print("\$AverageTemperature);

IT-SC bo

44