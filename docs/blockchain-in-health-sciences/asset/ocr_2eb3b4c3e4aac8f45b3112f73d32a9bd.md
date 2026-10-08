# BLOCKCHAIN IN HEALTH SCIENCES

```
CT = CT | d;
}
return CT, Sign(CT);
```

Following that, the CT and sCT are combined and directed toward Aggregation terminal.

# ii.    Phase 3: Data Aggregation

At this point, patient data has been collected from numerous Internet of Things devices is compiled and decoded. The aggregation terminal is where the decryptIoT and aggregateData algorithms are run. decryptIoT(CTs, sCTs, t, NP) ->(M)

After receiving inputs, this algorithm outputs a Raw Data String. The algorithmic detail is presented as follows:
decryptIoT(List<String> CTs, List<String> sCTs, String t, NP, String k): String { List<String> validCTs = [];
OTPad = Fad(t | NP);
For each CTs, as c, s {
If (Hash(c) == s {
validCTs.append(c);
}
For each validCTs as c {
k = k ⊕ c;
}
return k ⊕ OTPad;

The Aggregation Terminal saves the raw data and the time stamp of the IoT devices after each decryptIoT function execution. If sufficient raw data has been collected, the authorized user can bundle all of the raw data using the aggregate Data approach and add extra remarks to the data. aggregateData(Ms, AD)->(D)

The method concatenates an array of strings Ms with a string AD to produce string D for encryption.
Function aggregateData(List<String> Ms, String AD): String { String D = "";
ForEach Ms as m {