# EV Charger OCPP Compatibility

This repository maintains a list of Electric Vehicle (EV) chargers and their compatibility with the Open Charge Point Protocol (OCPP). It includes information on the supported OCPP versions and whether the communication is direct or through the manufacturer's cloud. Contributions are welcome to keep this list up-to-date!

## Table of Contents

- [Contribution Guidelines](#contribution-guidelines)
  - [Via pull requests](#via-pull-requests)
  - [Via issues](#via-issues)
- [OCPP Versions](#ocpp-versions)
- [Communiction types](#communication-types)
  - [Cloud](#cloud)
  - [Direct](#direct)
- [EV Charger List](#ev-charger-list)
  - [ABB](#abb)
  - [Charge Amps](#charge-amps)
  - [go-e](#go-e)
  - [Zaptec](#zaptec)
- [Additional Resources](#additional-resources)
- [License](#license)

## Contribution Guidelines

To add or update an entry:

### Via pull requests
1. Fork this repository.
2. Edit the table under the appropriate brand or create a new brand section if necessary. Keep the branches in alphabetical order.
3. Submit a pull request with your changes.

### Via issues
1. Create a new issue from the [New Issue](https://github.com/kallioaleksi/charger-ocpp-support/issues/new/choose) page
2. Select the appropriate labels (`new-brand` or `new-charger` for adding information, `invalid` for correcting invalid information)

Please provide official sources or links to validate the information when possible.

If you are unable to fork this repository or use issues and still wish to contribute, you can email the author with the details at <aleksi+ocpp@kallio.cloud>

## OCPP Versions

### 1.6S (SOAP)

OCPP 1.6S (SOAP) is an early version of the Open Charge Point Protocol that utilizes the SOAP (Simple Object Access Protocol) for communication between EV chargers and central systems. It was designed to enable interoperability between different charging stations and networks, focusing on stability and security in data exchanges. [OCPP 1.6 Specification (SOAP)](https://www.openchargealliance.org/protocols/ocpp-16/).

### 1.6J (JSON)

OCPP 1.6J (JSON) is a variant of the OCPP 1.6 specification that replaces SOAP with JSON (JavaScript Object Notation) for lighter, more efficient data handling. This version provides the same core functionality as 1.6S but with faster communication, making it suitable for more modern applications. [OCPP 1.6 Specification (JSON)](https://www.openchargealliance.org/protocols/ocpp-16/).

### 2.0

OCPP 2.0 introduced significant improvements over previous versions, including support for more advanced use cases, enhanced security features, and better device management. It also brought new functionalities like improved transaction handling and customizable charging profiles, making it a more robust protocol for complex charging networks. [OCPP 2.0 Specification](https://www.openchargealliance.org/protocols/ocpp-20/).

### 2.0.1

OCPP 2.0.1 is an update to OCPP 2.0, addressing minor corrections and improvements while maintaining backward compatibility. It refines existing features and adds clarity to the protocol specifications, enhancing communication reliability between charge points and central systems. [OCPP 2.0.1 Specification](https://www.openchargealliance.org/protocols/ocpp-201/).

### 2.1

OCPP 2.1 is the latest version of the protocol, further expanding on the capabilities introduced in OCPP 2.0.1. This version includes additional security measures, refined device management, and support for new functionalities such as ISO 15118 integration, making it suitable for the evolving EV charging ecosystem. [OCPP 2.1 Specification](https://www.openchargealliance.org/protocols/ocpp-21/).

## Communication types

### Cloud

When the communication type is listed as ☁️ Cloud, it means that the charger doesn't communicate directly with the specified OCPP endpoint, but instead uses a different protocol (or it could be OCPP as well) to communicate with the manufacturer's cloud services, which will then connect to the OCPP endpoint and interact with the OCPP server. While this is a perfectly normal pattern, there are a few aspects that should be known to the end user.

* The charger's OCPP functionalities can not be used without a public internet connection, since all data goes through the manufacturer's cloud
* OCPP connectivity works only when the manufacturer's cloud works, i.e. if the manufacturer decides to end support, OCPP connectivity is lost
* All data passes through the manufacturer's cloud

### Direct

As opposed to the Cloud communication type, 🔌 Direct means that the charger connects to the specified OCPP endpoint directly, with the designated OCPP version, without any intermediaries.

* The charger can connect directly to local OCPP endpoints without public internet access
* OCPP functionality isn't dependant on support from the manufacturer, it's built in to the charger
* Data is sent as directly as possible to the OCPP endpoint

## EV Charger List

### ABB

| Model | OCPP Version | Communication | Notes | Source |
|-------------------|---------------|----------------------|-----------------------------------------|----------------------------------|
| ABB Terra AC Wallbox | 1.6J | 🔌 Direct |  | [OCPP Implementation Overview](https://library.e.abb.com/public/8f07987a3a284da6bf4e4f8f53cd6502/ABB_Terra_AC_Charger_OCPP1.6_ImplementationOverview%20_v1.8_FW1.6.6.pdf) \| [Terra AC Installation manual](https://library.e.abb.com/public/bab5dff6eb6d4459becee864124fe603/Terra%20AC%20Installation%20manual%20BCM.V3Y01.0-EN%20V006.pdf?x-sign=N4zuManms26ghdC6rFTB4bgdPTAmidsO/wkNAg7Vf9kTKIyzRCODk5BnUsFLP2aB) |

### Charge Amps

| Model | OCPP Version | Communication | Notes | Source |
|-------------------|---------------|----------------------|-----------------------------------------|----------------------------------|
| Charge Amps Aura | 1.6J | ☁️ Cloud / 🔌 Direct |  | [OCPP Migration document](https://wwwchargeampscom.cdn.triggerfish.cloud/uploads/2024/08/ChargeAmps_OCPP-Migration_V3_Admins-Users-20240829.pdf) |
| Charge Amps Dawn | 1.6J | ☁️ Cloud | Charger model not mentioned in OCPP migration docs, assuming cloud connection | Source needed! |
| Charge Amps Halo | 1.6J | ☁️ Cloud / 🔌 Direct |  | [OCPP Migration document](https://wwwchargeampscom.cdn.triggerfish.cloud/uploads/2024/08/ChargeAmps_OCPP-Migration_V3_Admins-Users-20240829.pdf) |


### go-e

| Model | OCPP Version | Communication | Notes | Source |
|-------------------|---------------|----------------------|-----------------------------------------|----------------------------------|
| go-e Charger Gemini 11 kW | 1.6J | 🔌 Direct |  | [Installation and operating manual](https://go-e.com/fileadmin/Support/Anleitungen/Englisch/go-e-charger-gemini-installation-and-operating-manual.pdf) |
| go-e Charger Gemini 22 kW | 1.6J | 🔌 Direct |  | [Installation and operating manual](https://go-e.com/fileadmin/Support/Anleitungen/Englisch/go-e-charger-gemini-installation-and-operating-manual.pdf) |
| go-e Charger Gemini 2.0 11 kW | 1.6J | 🔌 Direct |  | [Installation and operating manual](https://go-e.com/fileadmin/Support/Anleitungen/Englisch/go-e-charger-gemini-installation-and-operating-manual.pdf) |
| go-e Charger Gemini 2.0 22 kW | 1.6J | 🔌 Direct |  | [Installation and operating manual](https://go-e.com/fileadmin/Support/Anleitungen/Englisch/go-e-charger-gemini-installation-and-operating-manual.pdf) |
| go-e Charger Gemini Flex 11 kW | 1.6J | 🔌 Direct |  | [Installation and operating manual](https://go-e.com/fileadmin/Support/Anleitungen/Englisch/go-e-charger-gemini-flex-installation-and-operating-manual.pdf) |
| go-e Charger Gemini Flex 22 kW | 1.6J | 🔌 Direct |  | [Installation and operating manual](https://go-e.com/fileadmin/Support/Anleitungen/Englisch/go-e-charger-gemini-flex-installation-and-operating-manual.pdf) |
| go-e Charger Gemini Flex 2.0 11 kW | 1.6J | 🔌 Direct |  | [Installation and operating manual](https://go-e.com/fileadmin/Support/Anleitungen/Englisch/go-e-charger-gemini-flex-installation-and-operating-manual.pdf) |
| go-e Charger Gemini Flex 2.0 22 kW | 1.6J | 🔌 Direct |  | [Installation and operating manual](https://go-e.com/fileadmin/Support/Anleitungen/Englisch/go-e-charger-gemini-flex-installation-and-operating-manual.pdf) |
| go-e Charger PRO CABLE | 1.6J | 🔌 Direct |  | [Datasheet](https://go-e.com/fileadmin/Support/Anleitungen/Englisch/go-e-charger-pro-datasheet.pdf) |

### Zaptec

| Model | OCPP Version | Communication | Notes | Source |
|------------------|--------------|----------------|-----------------------------------------|----------------------------------|
| Zaptec Go | 1.6J | ☁️ Cloud / 🔌 Direct | Direct OCPP connection supported after firmware update | [Zaptec Info Hub](https://www.zaptec.com/info-hub/inside-zaptec/ocpp) |
| Zaptec Pro | 1.6J | ☁️ Cloud | | [Zaptec Help Center](https://help.zaptec.com/hc/en-001/articles/4530001974033-Zaptec-Cloud-and-OCPP-Integration#h_01HF9AAA8G4GPFEXEYDZX0HQM8) |

## Additional Resources

- [OCPP Official Documentation](https://www.openchargealliance.org/protocols/ocpp/)
- [OCPP FAQ](https://www.openchargealliance.org/protocols/ocpp/faq/)

## License

Charger OCPP Support (c) by Aleksi Kallio

Charger OCPP Support is licensed under a Creative Commons Attribution 4.0 International License.

You should have received a copy of the license along with this work. If not, see <https://creativecommons.org/licenses/by/4.0/>.
