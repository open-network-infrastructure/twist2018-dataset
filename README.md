Data from [The Things Network](https://thethingsnetwork.org) (TTN) gateways in Zürich, collected as part of ongoing research and originally provided by [Benedikt Hitz-Gamper](http://www.digitale-nachhaltigkeit.unibe.ch/about_us/persons/hitz_gamper_benedikt/index_eng.html) (Institute of Information Systems, University of Bern) for the [TWIST 2018](https://hack.twist2018.ch) hackathon.

Originally uploaded by @gnz and reformatted as [Geospatial](https://frictionlessdata.io/docs/publish-geo/) [Data Package](https://frictionlessdata.io/specs/) by @loleg

## Data files

### File `ttn_gateways.csv` (134 rows)

* `device_id`: unique key for device_id in table `ttn_measurements` (this is an internal key, not connected with TTN IDs)
* `eui_id`: id used by TTN to uniquely identify gateways
* `platform`: make/model of gateway if provided
* `category`: clustered value for `platform`
* `lat`/`lng`: location of gateway if provided
* `altitude`: altitute of gateway if provided
* `ETH_dist`: distance from gateway to ETH main building (selection criteria for gateways is < 20km)

### File `ttn_measurements.csv` (750926 rows)

* `id`: unique id
* `device_id`: key for `device_id` in table `ttn_gateways`
* `last_online`: last handshake of gateway with TTN backend
* `rx_ok`: number of packets received by this gateway (counter is never reset)
* `tx_in`: number of packets sent by this gateway (counter is never reset)
* `measured_at`: time of measurement

To decide whether a gateway is online, verify the difference of `measured_at - last_online`. If difference is smaller than 30 to 90 seconds, the gateway was online at this time.

*Note:*
Somethimes `last_online` is greater than `measured_at`, this has to do with the fact that the values get actually stored in the database after `measured_at` and sometimes even a newer `last_online` is available.

### Related datasets

* **TTN Mapper data dumps** (crowd-sourced network coverage measurements): https://ttnmapper.org/dumps/
* **Live data of the NOC API**: http://noc.thethingsnetwork.org:8085/api/v2/gateways/eui-[x]  (replace `[x]` with gateway EUI)
* **Ownership data** on https://github.com/ttn-zh/gateway-remote-config/

## Credit

Data part of ongoing research, provided by Benedikt Hitz-Gamper, Institute of Information Systems, University of Bern, benedikt.hitz@iwi.unibe.ch

## License

The content in this repository is licensed under the CC-BY-SA 4.0 License (see the [LICENSE](LICENSE) file for details) unless stated otherwise.

[![License: CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/80x15.png)](https://creativecommons.org/licenses/by-sa/4.0/)
