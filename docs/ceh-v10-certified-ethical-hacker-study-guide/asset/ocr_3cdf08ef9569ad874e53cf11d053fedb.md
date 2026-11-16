# recon-ng Keys

[recon-ng][default] > keys list

| Name | Value |
| --- | --- |
| bing_api | |
| builtwith_api | |
| censysio_id | |
| censysio_secret | |
| flickr_api | |
| fullcontact_api | |
| github_api | |
| google_api | |
| google_cse | |
| hashes_api | |
| ipinfodb_api | |
| jigsaw_api | |
| jigsaw_password | |
| jigsaw_username | |
| pwnedlist_api | |
| pwnedlist_iv | |
| pwnedlist_secret | |
| shodan_api | |
| twitter_api | 0DE6bQv89M2AApxCvzfx7AIpd |
| twitter_secret | jxhcaFu9FS8AK9g4m6N90RhkuCQ0P6A5ppgSdckOIf3zhD3cMK |

Now that we have the API key in place for Twitter, we can run the module. In order to run the module, we have to “use” it, meaning we load the module with the use command. Once it’s loaded, we have to set a source. In our case, the source is a text string, so it’s in quotes, telling recon-ng that we are using a text string for the source. The text string expected here is a user handle. The word _recon_ was selected somewhat randomly and it got results. Once that’s done, all we need to do is run the module. You can see loading the module, setting the source, and running it in the following code. The results from the module are truncated because there were quite a few of them and this is just to show you how to use the module.