```
} catch (Exception $e) {
// rollback the transaction
$objPDO->rollBack();
echo "Failed: " . $e->getMessage();
}
?>
```

This example assumes a connection is made to the DSN described by $strDSN. In turn, a transaction commences, which encapsulates two interdependent queries described by $strQuery1 and $strQuery2.

Should any error occur at any stage, an exception will be generated, thus preventing the execution of any further code. All those transactions that have been executed since the transaction being initiated will be rolled back (that is, undone).

Transactions are a huge topic in and of themselves, and a complete discussion is outside the scope of this chapter. However, you will undoubtedly encounter them again throughout your programming career, so it is hoped that this section has proven a useful primer.

# Constants

Throughout this chapter, you have seen numerous references to static constants exposed by the PDO class — such as PDO :: PARAM_STR, PDO :: ERRMODE_EXCEPTION, PDO :: FETCH_ASSOC, and more.

These constants are used to define column data types, specify different fetch modes, set operational properties and attributes, and change row retrieval cursor behavior.

A full list of constants can be found at www.php.net/manual/en/pdo.constants.php.

# Handling Errors

Any enterprise-grade application needs exceptional exception handling (pun intended). Although you can mitigate against errors caused by everyday events (such as users failing to enter a password correctly) by using simple techniques in your PHP code, it’s also a good idea to ensure that you’re coping gracefully with any unexpected eventualities that might arise as a result of your application’s communication with your underlying database. This would include failing to connect to the database in the first place; failed authentication; missing relations (tables and/or columns), constraint violations; and more — anything your PHP couldn’t know about on its own.

How you handle the existence of an error is up to you — but graceful degradation is the goal. In Chapter 20, you’ll learn more about quality assurance and its importance in your application. The mechanism you use to handle exceptions in your application plays a big part in achieving a high degree of quality.

By default, PDO operates in what is called silent mode. This means errors won’t be detected if you don’t explicitly look for them using the errorCode() and errorInfo() methods on either (or both) PDO or PDOStatement.