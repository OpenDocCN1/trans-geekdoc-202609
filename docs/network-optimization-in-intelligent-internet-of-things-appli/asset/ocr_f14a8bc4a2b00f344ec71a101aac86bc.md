# A Comprehensive IoT Security Framework Using Computing

Data filter and cloud integration
Public Class TempSensorApplication
(Initialise OPTIMAL_TEMP_LOW = 96.0)
(Initialise OPTIMAL_TEMP_HIGH = 99.5)
(Initialise Range<Double> optimalTempRange
OptimalRange = Ranges.clamped(Optimal_TEMP_LOW, OPTIMAL_TEMP_HIGH)
Public Static Void Main(String[] args) throws Exception
TempSensor sensor = new TempSensor ()
DirectiveProvider = new DirectiveProvider();
Topology topology = new Topology();
SendTO thinkspeak = new Send thinkspeak(sensor);
Stream.doubleread(templeads = topology.ports[sensor], Time
Unit.MILLISECONDS)
Stream.doubleread(filteredReadings = temoroReadings.filter(tuple ->noptimalTempRange.contains(tuple))
filteredReadings.sink(tuple -> System.out.println("normal
temperature exceeded") + "It is " + tuple + "\u0FF")
long time = System.nanoTime() - start
filteredReadings.sink(tuple -> speaks.sendDataOverRes(tuple))
templeads.print()); }

# Body temperature assessment using EH-IoT

```
Public Class TempSensor Implements Supplier<>
(static Final Long SerialVersionUID=L, raw_data,str;
@Override Public Double Get()
[Serialport] ports = SerialPort.getCommPorts();
[Serialport] serialPort = ports[chosenPort - 1];
try { SerialPort.setComPortParameter(9600, 5, 1,
Port.NO_PARITY);
@SupressWarnings("resource")
Scanner = new Scanner(serialPort.getInputStream());
if(data.hasNextLine())
{ str = data.next();
raw_data = Double.parseDouble(str);
} catch (Exception ) { serialPort.close(); return
(raw_data); }
```

FIGURE 16.6 (a and b) EH-IoT model for measuring body temperature, data filters, and cloud integration.