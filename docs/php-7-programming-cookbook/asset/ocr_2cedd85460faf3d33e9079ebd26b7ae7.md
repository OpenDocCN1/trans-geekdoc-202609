# Chapter 11

```
ed@ed: ~/Desktop/repos/php7_recipe/source/chapter11
SQL Statements:
SELECT email,first_name,last_name,status,address,city,state,province,postal_code,phone,country_id,id FROM prospects_11
INSERT INTO customer_11 ( email,name,status,level,password,id,profile_id ) VALUES ( :email, :name, :status, :level, :password, :id, :profile_id )
INSERT INTO profile_11 ( address,city,state,province,postal_code,phone,country,photo, :id ) VALUES ( :address,:city,:state_province,:postal_code,:phone,:country,:photo,:id,:id )
Processing: WILFREDO RICHARDS
Processing: WILLARD ATKINSON
Processing: MANUEL WHITE
Processing: EDGAR SLOAN
Processing: AARON ALSTON
Processing: JEFF CASTRO
Processing: NEAL CHAVEZ
Processing: LEONARD LOVE
Processing: ROLANDO LANDRY
Processing: FREDRICK BEASLEY
Processing: RANDAL STUART
Processing: DARRYL LAWSON
Processing: SEAN DOMINGUEZ
Processing: CARLTON McCALIN
```

We can then view the data directly from the database using SQL JOIN to ensure the relationship has been maintained:

![](bbox=[0.17, 0.48, 0.81, 0.82])

417