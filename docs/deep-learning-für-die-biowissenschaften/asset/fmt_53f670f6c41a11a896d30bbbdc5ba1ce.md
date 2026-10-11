
# RNA: Mehr als nur ein Informationsüberträger

Konventionell wird RNA nur als Informationsüberträger angesehen, aber bereits in den Anfängen der Genomikforschung wussten Biologen, dass dies nicht ganz richtig ist. Die Übersetzung von `mRNA` in Proteine erfolgt durch `Ribosome`, komplizierte molekulare Maschinen, die aus Proteinen und RNA bestehen. Eine weitere Schlüsselrolle bei der Translation spielen Moleküle namens `Transfer-RNA` (oder kurz `tRNA`). Diese Moleküle definieren den »genetischen Code«, indem sie Muster von drei Basen in der `mRNA` erkennen und die richtige Aminosäure zum wachsenden Protein hinzufügen. Seit über einem halben Jahrhundert wissen wir, dass es mindestens drei Arten von RNA gibt: `mRNA`, ribosomale RNA und `tRNA`.

Aber RNA kann noch mehr. Es ist ein überraschend vielseitiges Molekül. In den letzten Jahrzehnten wurden viele weitere RNA-Arten entdeckt. Einige Beispiele:

*   `microRNAs` (`miRNAs`) sind kurze RNA-Stücke, die an `mRNAs` binden und verhindern, dass diese in Proteine übersetzt werden. Das ist ein sehr wichtiger Regulationsmechanismus bei einigen Tierarten, vor allem bei Säugetieren.
*   `Short interfering RNA` (`siRNA`) ist eine weitere RNA-Art, die an `mRNA` bindet und verhindert, dass diese übersetzt wird. Sie ist der `miRNA` ähnlich, besteht jedoch aus einem Doppelstrang (im Gegensatz zu `miRNAs`, die nur aus einem einzelnen Strang bestehen) und unterscheidet sich auch in der Funktionsweise. Wir werden die `siRNA` im Verlauf des Kapitels noch genauer betrachten.
*   `Ribozyme` sind RNA-Moleküle, die wie Enzyme chemische Reaktionen katalysieren. Chemie ist die Grundlage für alles, was in einer lebenden Zelle geschieht. Katalysatoren sind daher lebenswichtig. Normalerweise übernehmen Proteine diese Funktion, nun wissen wir, dass manchmal auch die RNA das übernimmt.
*   Bei `Riboswitches` handelt es sich um RNA-Moleküle, die aus zwei Teilen bestehen. Ein Teil fungiert als `mRNA`, während der andere in der Lage ist, an kleine Moleküle zu binden. Bei der Bindung wird die Translation der `mRNA` entweder ermöglicht oder verhindert. Dies ist noch mal ein weiterer Regulationsmechanismus, durch den die Proteinproduktion anhand der Konzentration bestimmter kleiner Moleküle in der Zelle angepasst wird.

Selbstverständlich müssen alle diese unterschiedlichen RNAs hergestellt werden, und die DNA enthält die entsprechenden Baupläne. Somit ist die DNA mehr als nur eine Kette codierter Proteinsequenzen. Sie enthält auch RNA-Sequenzen, Andockstellen für `Transkriptionsfaktoren` und andere Regulationsmoleküle, Anweisungen dazu, wie `mRNAs` gespliced werden sollen, und verschiedene chemische Modifikationen, die beeinflussen, wie sie um Histone gewickelt wird und welche Gene transkribiert werden.

Was passiert, nachdem das Ribosom die `mRNA` in ein Protein umgewandelt hat? Einige Proteine können sich selbsttätig in die richtige 3-D-Form falten, viele weitere jedoch benötigen die Hilfe von Proteinen, die `Chaperone` genannt werden. Sehr häufig benötigen Proteine nach der Translation zusätzliche chemische Modifikationen. Anschließend muss das fertige Protein an die Stelle in der Zelle transportiert werden, an der es seine Arbeit verrichten kann, bevor es abgebaut wird, wenn es nicht mehr benötigt wird. Jeder dieser Prozesse wird durch zusätzliche Regulationsmechanismen kontrolliert und beinhaltet Interaktionen mit vielen anderen Molekülen.

Sollte das überwältigend klingen, liegt es daran, dass es das ist! Ein lebender Organismus ist deutlich komplizierter als jede Maschine, die der Mensch je gebaut hat. Der Gedanke, das zu verstehen, *sollte* Sie einschüchtern!

Aus diesem Grund ist Machine Learning aber auch so ein mächtiges Werkzeug. Wir haben riesige Datenmengen, die durch einen Prozess generiert werden, der unglaublich komplex und gleichzeitig kaum verstanden ist. Wir wollen subtile Muster erkennen, die in den Daten vergraben sind. Das ist genau die Art von Aufgabe, bei der sich Deep Learning hervortut!

Tatsächlich eignet sich Deep Learning hervorragend für diese Aufgabenstellung. Klassische statistische Methoden haben Mühe, die Komplexität des Genoms darzustellen. Häufig basieren sie auf der Vereinfachung von Annahmen. Beispielsweise suchen sie nach linearen Beziehungen zwischen Variablen oder versuchen, die abhängige Variable nur anhand einiger weniger anderer Variablen zu modellieren. Die Genomik jedoch enthält komplexe, nicht lineare Beziehungen zwischen Hunderten Variablen: genau die Art von Beziehung, die von einem Deep Neural Network effektiv beschrieben werden kann.

## Transkriptionsfaktor-Bindung

Als Anwendungsbeispiel der Genomik werden wir mithilfe von Deep Learning das Problem der Bindung von Transkriptionsfaktoren betrachten. Wie bereits erwähnt, sind `TFs` Proteine, die an DNA binden. Durch die Bindung beeinflussen sie die Wahrscheinlichkeit, dass nahe gelegene Gene in RNA transkribiert werden. Woher weiß aber ein `TF`, wo er binden muss? Wie so oft in der Genetik hat diese Frage eine einfache Antwort, die von vielen Komplikationen begleitet wird.

Jeder `TF` hat eine spezifische DNA-Sequenz, die als *Bindungsstellenmotiv* bezeichnet wird, an die er bindet. Bindungsstellenmotive sind in der Regel kurz, üblicherweise bestehen sie aus zehn Basen oder weniger. Wo auch immer das Motiv eines `TF` im Genom vorkommt, bindet der `TF` daran.

In der Praxis sind die Motive jedoch nicht ganz spezifisch. Ein `TF` kann an viele ähnliche, aber nicht identische Sequenzen binden. Einige Basen innerhalb des Motivs könnten wichtiger sein als andere. Dies wird häufig als *Positions-Gewichts-Matrix* modelliert, die angibt, welche Vorliebe der `TF` für jede mögliche Base an jeder Position innerhalb des Motivs hat. Das setzt natürlich voraus, dass jede Position innerhalb des Motivs unabhängig ist, was nicht immer der Fall ist. Manchmal variiert sogar die Motivlänge. Und obwohl die Bindung in erster Linie von den Basen innerhalb des Motivs bestimmt wird, kann die DNA ebenfalls einen gewissen Einfluss haben.

Und wir haben bisher nur die Sequenz berücksichtigt! Andere Aspekte der DNA können ebenfalls wichtig sein. Viele `TFs` werden durch die physische Form der DNA beeinflusst, z. B. wie eng die Doppelhelix verdreht ist. Methylierte DNA kann ebenfalls die `TF`-Bindung beeinflussen. Und vergessen Sie nicht, dass der größte Teil der DNA in Eukaryoten dicht gepackt und um Histone gewickelt ist. `TFs` können nur an die Abschnitte binden, die abgewickelt wurden.

Andere Moleküle spielen ebenfalls wichtige Rollen. `TFs` interagieren oft mit anderen Molekülen, und diese Interaktionen können die DNA-Bindung beeinflussen. Beispielsweise kann ein `TF` an ein weiteres Molekül binden, und der so gebildete Komplex bindet dann an ein anderes DNA-Motiv als der `TF` allein.

Biologen haben Jahrzehnte damit verbracht, diese Details zu entwirren und Modelle für die `TF`-Bindung zu entwickeln. Wir werden stattdessen versuchen, mithilfe von Deep Learning ein Modell anhand der Daten zu entwickeln.

### Ein Konvolutionsmodell für die TF-Bindung

In diesem Beispiel verwenden wir experimentelle Daten des Transkriptionsfaktors `JUND`. Ein Experiment wurde durchgeführt, um jede Stelle des menschlichen Genoms zu identifizieren, an der es bindet. Zur besseren Übersicht verwenden wir nur die Daten von Chromosom 22, einem der kleinsten Chromosomen des Menschen. Dennoch ist es 50 Millionen Basen lang, sodass wir ausreichend Daten haben, mit denen wir arbeiten können. Das gesamte Chromosom wurde in kürzere Abschnitte mit jeweils 101 Basen aufgeteilt, und es wurde gekennzeichnet, ob es eine Bindungsstelle für `JUND` enthält oder nicht. Wir werden ein Modell trainieren, das diese Labels basierend auf der Reihenfolge der einzelnen Abschnitte vorhersagt.

Die Abschnitte werden mit der One-Hot-Codierung dargestellt. Für jede Base haben wir vier Zahlen, von denen eine auf 1 und die anderen auf 0 gesetzt sind. Ob es sich bei der Base um `A`, `C`, `G` oder `T` handelt, wird durch die 1 angezeigt.
