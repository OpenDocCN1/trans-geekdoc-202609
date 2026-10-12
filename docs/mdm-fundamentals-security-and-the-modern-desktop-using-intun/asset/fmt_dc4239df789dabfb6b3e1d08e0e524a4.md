
### Test 2: When MDMWinsOverGP is Not Configured, set the Group Policy setting to Enabled, then the corresponding MDM setting to Disabled.

In this test, Group Policy value will be set first and set to Enabled. Then MDM will set the same value as Disabled.

1. Create and link a GPO that would **Enable** Cortana.
2. Refresh Group Policy and verify that Cortana is, in fact, enabled.
3. Create MDM policy to **Disable** Cortana.
4. Assign MDM policy to Win10 1809 device. Refresh MDM.

* **Test 2 results:** `Cortana` remains Enabled. Feels like MDM loses.

This feels like the correct result.

Group Policy got there first, `MDMWinsOverGP` is Not Configured (or specifically set to Disabled to lose). And what happens? The Group Policy setting you expected was on the box.

### Test 3: When MDMWinsOverGP is Enabled, set the Group Policy setting to Enabled, then the corresponding MDM setting to Disabled.

1. Create and link a GPO that would **Enable** Cortana.
2. Refresh Group Policy and verify that Cortana is, in fact, enabled.
3. Create MDM policy to **Disable** Cortana.
4. Assign MDM policy to Win10 1809 device. Refresh MDM.

* **Test 3 results:** `Cortana` becomes disabled. MDM wins.

This also feels like the correct result.

Group Policy got there first; `MDMWinsOverGP` is set to Enabled (to win). And what happens? The MDM setting written second overrides the Group Policy setting, and the MDM setting you expected was on the box.

In case your head is swimming a little bit, here’s a table showing a grid which enumerates the key cases in an easy-to-digest format.

| Case | MDMWinsOverGP | MDM Value | Group Policy Value | Item State | Result / Feeling |
| --- | --- | --- | --- | --- | --- |
| 1 | Not set or 0 (Disabled) | Disabled | Enabled | Can’t know. | Can’t know. |
| 2 | Not set or 0 (Disabled) | Enabled | Disabled | Can’t know. | Can’t know. |
| 3 | Not set or 0 (Disabled) | Disabled | Enabled | Can’t know. | Can’t know. |
| 4 | Not Set or 0 (Disabled) | Enabled | Disabled | Can’t know. | Can’t know. |
| 5 | Set to 1 (MDM wins) | Disabled | Enabled | Disabled | MDM wins. |
| 6 | Set to 1 (MDM wins) | Enabled | Disabled | Enabled | MDM wins. |
| 7 | Set to 1 (MDM wins) | Disabled | Enabled | Disabled | MDM wins. |
| 8 | Set to 1 (MDM wins) | Enabled | Disabled | Enabled | MDM wins. |

So how do we interpret these seemingly contradictory results?

* `MDMWinsOverGP` is *not* a two-way street. It is only for controlling when MDM wins over GPO. It is not about controlling when GPO wins over MDM.
* If `MDMWinsOverGP` is not configured (or Disabled), Group Policy versus MDM world is non-deterministic.

Non-deterministic is just a fancy way of saying you might not be able to predict what is going to happen over the long haul.

Why is this?

Well, in the real world, sometimes you’re going to have Group Policy settings that were applied first; then MDM settings are going to apply second. Sometimes you’re going to have MDM settings apply first, and Group Policy settings are going to apply second.

As of right now, here are the final rules of the game if you want to attempt to make your MDM and Group Policy co-managed world to be as deterministic as possible:

* Turn on the value to force MDM to win over Group Policy (`./Vendor/MSFT/Policy/Config/ControlPolicyConflict/MdmWinsOverGp` to 1).
* Use MDM to define policies whenever possible.
* Actively avoid Group Policy versus MDM conflicts for good measure, though with the `MdmWinsOverGP` set to 1, the engine will make MDM win in a conflict when the same MDM value is set against the same Group Policy setting.
* Use Group Policy for those setting that cannot be configured by MDM “First class” settings. You can always back out of a Group Policy ADMX setting easily, should that value become a first class setting within MDM.

#### MdmWinsOverGp: Final Thoughts and Notes

As I said, I believe this complicated “non-deterministic” behavior will have to be eventually rectified. I have no insider knowledge, and no one is telling me anything as I write this; it’s just a hunch. But here’s what I think could happen:

* Microsoft could change the default to `MDMWinsOverGP` set to “on” and therefore MDM would just win over a Group Policy conflict. (Again, this would only kick in when the Group Policy value is also deployed to the same target value anyway.)
* Microsoft could make it more deterministic when `MDMWinsOverGP` is not set. They could just decide that “whoever gets there first” is the expected behavior, until `MDMWinsOverGP` is set.

Again, no timeline yet, because no one is telling me anything. But in some future world, these are two possibilities. There are likely other things that the engine could do to help resolve and report conflicts.

Since I cannot predict the future, I promise to write about it on `MDMandGPanswers.com`. But then beyond that, you can read more about this at:

`https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-controlpolicyconflict`

You may want to check this website every time Windows ships an update, because it might be irrelevant if Microsoft just “goes ahead” and makes MDM win over Group Policy…always. My guess is that this page will tell you in what version of Windows this will have transpired.

Two other good write-ups on this subject can be found here:

`https://osddeployment.dk/2018/02/12/how-to-control-both-mdm-and-gpo-settings-on-windows-10/`

`https://blogs.technet.microsoft.com/cbernier/2018/04/02/windows-10-group-policy-vs-intune-mdm-policy-who-wins/`

### What Is Microsoft Azure AD Domain Services (and What Does It Have to Do with Group Policy)?

Don’t get confused about real on-prem Group Policy with your MDM service and another, completely unrelated idea called Microsoft Azure AD Domain Services (AADDC for short).

AADDC is a way to make a “pretend” domain in the cloud for your existing on-prem servers to leverage if you decide to “lift and shift” some of your servers to Azure. And, when inside Azure, they still need to talk to something that is pretending to be a domain. So AADDC helps these machines join something…it’s like a mini-real on-prem AD domain, but in the cloud.

But for 10000% clarity: This mini on-prem AD domain in the cloud is not for Windows 10 machines to join but instead only for servers to join.

I explain this concept here only so you don’t search for, say, “Joining Azure AD and Group Policy” and come across AADDC and wonder, “What the heck is this thing?”

And when you see AADDC, you’ll see information about managing these servers with AADDC’s built-in Group Policy editor—again, to manage those servers that would usually be managed on-prem with AD and Group Policy.

In short: This AADDC thing is only for servers and not for endpoints.

Now you know.

So AADDC’s URL to learn more is:

`https://docs.microsoft.com/en-us/azure/active-directory-domain-services/active-directory-ds-admin-guide-administer-group-policy`

## Final Thoughts

Even if you don’t have SCCM, you’re going to hear a lot from Microsoft about co-management. Sometimes, I’m hearing them also say, “Cloud attached,” as in, “You can get your on-prem infrastructure ‘Cloud Attached’ and then co-manage your environment with SCCM and Intune.” I don’t know if Microsoft is going to stick with that phrasing, but I thought I should mention it in case you hear it.

And, since you likely have on-prem AD and Group Policy, it’s good to know all about Co-Policy management (my phrase, not Microsoft’s) and about working together.

Remember, to ensure that the values are deterministic, you must flip the switch to make MDM specifically win over Group Policy or else you literally cannot know the final state of the machine.
