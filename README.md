# AMRIT - Scheduler
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)  [![DeepWiki](https://img.shields.io/badge/DeepWiki-PSMRI%2FScheduler--UI-blue)](https://deepwiki.com/PSMRI/Scheduler-UI)


It acts as an interface between client and the scheduling services provided, allowing users to interact for consultation with specialists. It also provides the info of availability and unavailability of specialists, retrieving available slots for specialists, booking and cancelling slots, and fetching day views of specialists for a particular specialization.

### Features
* Handles various requests for scheduling/booking/cancelling slots
* Provides slots availability
* provides specialists availability of any day

## Prerequisite
* JDK 17
* Maven 
* Nodejs v18.10.0
* MySQL

## Run
* npm install -g @angular/cli@16.2.10
* npm install typescript@5.1.3 --save-dev
* npm install
* npm run build
* mvn clean install
* npm start

## Building from source

1. To build deployable war files
```bash
mvn -B package --file pom.xml -P <profile_name>
```

The available profiles include dev, local, test, and ci.
Refer to `src/environments/environment.ci.template` file and ensure that the right environment variables are set for the build.

Packing with `ci` profile calls `build-ci` script in `package.json`.
It creates a `environment.ci.ts` file with all environment variables used in the generated build.

## Filing Issues

If you encounter any issues, bugs, or have feature requests, please file them in the [main AMRIT repository](https://github.com/PSMRI/AMRIT/issues). Centralizing all feedback helps us streamline improvements and address concerns efficiently.  

## Join Our Community

We’d love to have you join our community discussions and get real-time support!  
Join our [Discord server](https://discord.gg/FVQWsf5ENS) to connect with contributors, ask questions, and stay updated.  

