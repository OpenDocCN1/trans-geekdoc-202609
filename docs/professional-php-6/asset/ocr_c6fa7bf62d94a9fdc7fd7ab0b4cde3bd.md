```
$this->errorCode = 2;
	$mtp->disconnect();
	return(false);
	}

	if (PEAR::isError($mtp->mailFrom(
		$this->objApparentSender->getStringRepresentation())))) {
		$this->strErrorMessage = "Unable to set sender";
		$this->errorCode = 3;
		$mtp->disconnect();
		return(false);
	}

	// Send to each recipient
	foreach ($this->arRecipientCollection as $strRecipientIdentifier =>
					$objEmailRecipient) {
		$strThisAddress = $objEmailRecipient->getRecipientAddress();
		if (PEAR::isError($res = $mtp->rcptTo($strThisAddress))) {
			$this->strErrorMessage = "Unable to add recipient " . $strThisAddress;
			$this->errorCode = 4;
			$mtp->disconnect();
			return(false);
		}
	};

	if (PEAR::isError($mtp->data($strFullEmail))) {
		$this->strErrorMessage = "Unable to send data to server";
		$this->errorCode = 5;
		$mtp->disconnect();
		return(false);
	}
	$mtp->disconnect();
	return(true);
}
};
```

Note a few things about this approach. First, when a recipient is added as the primary recipient or a member of the carbon copy (Cc) list, you can add the recipient to the collection held in the parent superclass, and then clone the recipient object before adding to the list of apparent recipients. This step isn't vital, but it means that you can implement your own `clone()` method in your `EmailRecipient` class, if you want, to modify the behavior taken when this copy is made.

Second, this example uses the error code and error message member variables of the `Communication` superclass. These are accessible through public functions. You can use these to debug your applications. E-mail can be an unpredictable phenomenon at times, and failure can occur through any number of scenarios, including a failure to reach the SMTP server, being denied permission to send e-mail to your particular IP address, or having a recipient be rejected outright by the SMTP server.

Third, the code `date("D, M j H:i:s T Y O")` is used to construct the e-mail header's date property. A quick glance at the PHP documentation reminds you that this produces a timestamp in the format `Tue, Jul 20 22:58:58 BST 2004 +0100`, which is the format required in e-mail headers.