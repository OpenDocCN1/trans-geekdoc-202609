
# How exactly tethering is enabled depends on the operating system and the particular configuration settings therein

Android OS devices can complicate matters because with each update, the OEM or carrier may customize the device further. One security concern that is key to this discussion is the unauthorized remote activation/deactivation of devices or features. Given how easily tethering can be used to connect an unmanaged device to the network, you should remain vigilant and monitor tethering from unauthorized activations.

## Airplane Mode

If you have flown recently, you know that on every flight you are reminded to place any cellular device in airplane mode before the plane taxis down the runway. FCC regulations ban the use of cell phones in order to protect instrumentation in the cockpit. At 20,000 feet in the air, active cell phones could pick up service from cell towers on the ground, as well as stop scanning for nearby Wi-Fi networks and attempt to join them. Years ago, some models of the Boeing 737 were found to be sensitive to radio interference from phones. This is the same reason you are not supposed to use cell phones in some parts of hospitals.

Airplane mode also disables Bluetooth and GPS. Airplane mode can block your device from attacks and protect privacy. Turning airplane mode on keeps applications from reporting the location of the device.

## Location Services

Mobile devices store and sometimes share geolocation data. Location services make life easier by guiding us to the nearest Starbucks, but how are vendors using this information and how might they monetize it? Accumulating all this information over time lets a company create a detailed profile of your behavior and preferences. If this information is accessed by someone with nefarious intentions, it could become a security threat. Criminals have used this information to steal identities, and law enforcement has used location data to track innocent people such as those who happened to be in the vicinity of a crime.

## DNS over HTTPS

Domain Name System (DNS) is the service that lets people find what they're looking for on the Internet. DNS operates behind every address translation, working to resolve fully qualified domain names (FQDNs) and human-readable addressing into numeric IP addresses. DNS serves a critical function for people. If DNS as a service were to cease, the Internet would continue, but users would need to know the IP address of every site they wanted to visit. DNS is a request-response protocol. When a DNS server sends a response to a request, the reply message contains the transaction ID and questions from the original request as well as any answers that it was able to find.

DNS over HTTPS (DoH) is a protocol for performing remote DNS via HTTPS to increase privacy and security. Some organizations also use DNS over TLS (DoT) for encrypting DNS queries. `Custom DNS` allows people to specify the IP address of the faster or more reliable DNS server they want to use by using special settings that allow them to specify what DNS resolvers to use. It is very useful when you want to block specific types of ads or trackers, as well as filtering websites.

# Deployment Scenarios

Given how affordable it is to own a mobile device, or several devices, organizations have been forced to decide how to regulate employees' selection of mobile devices at work. The principal decision is clear: can an employee use their own device or not? The pros and cons are not quite as clear, but what follows are the popular choices and consequences with which every CASP+ should be familiar.

## COBO

`Corporate-owned, business only (COBO)` devices were the norm before nearly everyone had their own mobile device. COBO means a company not only dictates your choice of mobile device but also enforces its content and use. While not a Draconian policy, it certainly seems rigid when compared to companies supporting users to install their choice of applications or even bring their own device. The COBO policy is rigid but secure, offering no flexibility or latitude to users, and mobile devices can be managed more closely than with any of the other options.

## COPE

`Corporate-owned, personally enabled (COPE)` is one step removed from COBO. It appeases users greatly by offering more freedom in mobile device usage, perhaps allowing independence in application, installation, and browsing. Exactly how much independence is allowed can be controlled to varying degrees, but in the end security is of greater concern than with COBO.

## CYOD

With `choose your own device (CYOD)`, an organization offers its users a choice among a small number of approved mobile devices. CYOD is a compromise for employees who are loyal to a particular mobile operating system. It's understandable that people can become accustomed to one type of device or another, so CYOD is a solution that offers a couple of models that use one of the popular mobile OSs.

CYOD doesn't necessarily mean that users have the freedom to install any application they like. It is more about giving the choice of which platform, and perhaps which set of features, appeals to employees.

## BYOD

If you ask most employees, they will choose the option to bring their own device to work. An organization with a `bring your own device (BYOD)` policy in place offers its employees the greatest degree of flexibility and variety in what mobile device they want to use. Based on recent statistics, it seems that between 60 and 70 percent of organizations have a BYOD policy in place. More details on these different approaches, including their popularity, can be found here: `www.techtarget.com/searchmobilecomputing/feature/BYOD-vs-COPE-Why-corporate-device-ownership-could-make-a-comeback`.

By being a CASP+ candidate, you already know that allowing users to bring their own devices to work poses the greatest risks and security concerns to the organization. BYOD risks are not mitigated by using standard configuration profiles or standardized device management, but more through management of access control and network and resource connections.

# Mobile Device Security Considerations

If one thing is constant, it's that attackers continually look for new methods of attack. Emergent threats are those that are becoming more prominent and were not seen in the past. These threats include the following:

*   **Smartphone Attacks** Smartphones are much more powerful than they were just a few years ago, and today they are just very small, powerful computers. They are an appealing target for attackers. Although some have sounded the alarm for smartphone viruses, worms, and bots for a number of years, these threats have yet to reveal themselves in a major way. Several factors have contributed to the slower than expected advancement of this category of malware. These factors include lack of bandwidth, a fragmented market, and a much shorter life cycle for smartphones than for a computer.
