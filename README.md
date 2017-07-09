## Sonoff-Angel
Sonoff-Angel firmware is a fork off Sonoff-Tasmota which hardens usage of dangerous MQTT routines in order to have a more secure, out-of-the-box, firmware experience.

That said - there is no particular hardeining except MQTT protocol starilizations, which omits dangerous method usages from the code base.

In particular - "Angel edition" eliminates the usage of those commands:
1. cmnd/sonoff/AP
1. cmnd/sonoff/Status 2
1. cmnd/sonoff/SSId
1. cmnd/sonoff/Password
1. cmnd/sonoff/WebServer
1. cmnd/sonoff/WebConfig
1. cmnd/sonoff/MqttClient
1. cmnd/sonoff/MqttHost
1. cmnd/sonoff/MqttUser
1. cmnd/sonoff/MqttPassword
1. cmnd/sonoff/otaUrl
1. cmnd/sonoff/Upgrade
1. cmnd/sonoff/Upload



Current version is **5.2.4** - See [sonoff/_releasenotes.ino](https://github.com/arendst/Sonoff-Tasmota/blob/master/sonoff/_releasenotes.ino) for change information.

## What about the Robin hood scenario?
As the original version of sonoff is wildly used and found to be able to be exploited over MQTT while the broker is connected promiscuously to the internet - this version can be implemented by sucessfuly exploiting the otaUrl parameter overwrite and then Upgrade/Upload triggering in order to control the box - one can be a Robin Hood of sorts and hack those devices in order to bring "Aangel" into working, a wise hacker would be able to do so without harming configuration and keeping all other functionalities intact.

As I perceive that this scenario is possible - I do not encourage that by any means as this, albeit being righteous, is illegal over the globe.

## Is Angel is the only option to defend Sonoff's vulnerable MQTT topics?

NO.

It is neither the only nor the best option to harden your systems but in many cases can be the easiest method because of the complexity of implementing a broker-centric permission scheme over known topics which can be changed and are, in times, hard to interpret correctly.

In particular - one can enact a policy on the broker with a similar fashion to disallowing anonymous connections and authorizing user per topic per publish method, and one should be able to subscribe to stat/sonoff/RESULT without proper authentication as well.
