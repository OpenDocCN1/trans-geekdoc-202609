154

Blockchain

### ALGORITHM 2 UPDATE HASH OF EMERGENCY RECORDS
Inputs: PID, Hemergency
Output: Hemergency of PatientPID is updated

1. if number of inputs is 2 then
2. Create an empty EHR structure "EHR_sample"
3. EHR_sample = GetState(PID)
4. EHR_Sample.hash_emergency = Hemergency
5. PutState(EHR_Sample.P_ID, EHR_Sample)
8. else
9. return Error;
10. end

### ALGORITHM 3 UPDATE HASH OF ENCRYPTED RECORDS
Inputs: PID, Hencrypted
Output: Hencrypted of PatientPID is updated

1. if number of inputs is 2 then
2. Create an empty EHR structure "EHR_sample"
3. EHR_sample = GetState(PID)
4. EHR_Sample.hash_encrypted = Hencrypted
5. PutState(EHR_Sample.P_ID, EHR_Sample)
8. else
9. return Error;
10. end

### ALGORITHM 4 GET HASH OF ENCRYPTED RECORDS
Inputs: PID
Output: Hencrypted of PatientPID

1. if number of inputs is 1 then
2. Create an empty EHR structure "EHR_sample"
3. EHR_sample = GetState(PID)
4. return(EHR_Sample.hash_encrypted)
5. else