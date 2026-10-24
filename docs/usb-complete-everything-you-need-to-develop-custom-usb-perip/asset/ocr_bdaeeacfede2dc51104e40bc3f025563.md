```
else
  ' The PICMicro is ready to send a byte.
  ' Find out if the '245BM is ready to receive a byte.
  if (TXE = 0) then
    ' TXE = 0, indicating that the '245BM is ready
    ' to receive a byte.
    ' Configure the data port's bits as outputs.
    data_port_direction = OUTPUTS
    ' Write the byte to the data port.
    data_port = data_out
    ' Bring WR high, then low, to cause the '245BM
    ' to read the byte.
    WR = 1
    WR = 0
    'The PICMicro is now ready to receive a byte.
    read_or_write = 1
  endif
endif
GoTo loop
```

Listing 14-2: PICBasic Pro code to enable a PICMicro 16F877 to read a byte from an FTDI FT245BM (Sheet 3 of 4).