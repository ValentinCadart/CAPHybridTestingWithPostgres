# CAP Hybrid Testing with Postgres on SAP BTP application 

[![CAP][CAP]][CAP-url] &emsp; [![SAPFE][SAPFE]][SAPFE-url] &emsp; [![Postgresql][Postgresql]][Postgresql-url] 



This is a sample SAP CAP (Node.js) project demonstrating hybrid testing with a PostgreSQL database on SAP BTP. It includes the SSH tunneling setup required to run the application locally from Business Application Studio while accessing real data.

The project is based on the sample application from the [official CAP deployment guide](https://cap.cloud.sap/docs/guides/deployment/to-cf).

## Run

Follow these steps to run the project locally in hybrid mode:

1. **Install dependencies**

   Make sure you have Node.js installed and then run: test

   ```bash
   npm install 

2. **Build and deploy the project on SAP BTP**
  
   Freeze dependencies, build and deploy the app using:

   ```bash
   cds up 

3. **Enable SSH on your Cloud Foundry application**

    Run the following commands to enable SSH access:

   ```bash
   cf enable-ssh bookshop-srv
   cf restart bookshop-srv

4. **Create an SSH tunnel**

   In your first terminal in BAS, forward the local port to the remote PostgreSQL instance:

   ```bash
   cf ssh -L 63306:<host_from_service_key>:<port_from_service_key> <application_name>
   ```

    Replace the placeholders with the appropriate values from your PostgreSQL service key and the name of the deployed application.

5. **Run the application with the hybrid profile**

    In a second terminal, start your app in hybrid mode:

   ```bash
   cds watch --profile hybrid 
   ```
   You should see confirmation that it connects to PostgreSQL on 127.0.0.1:63306




<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
<!-- https://simpleicons.org/ -->
[SAPFE]: https://img.shields.io/badge/SAP%20Fiori%20Elements-0FAAFF?style=for-the-badge&logo=sap&logoColor=white  
[SAPFE-url]: https://sapui5.hana.ondemand.com/sdk/#/topic/03265b0408e2432c9571d6b3feb6b1fd
[CAP]: https://img.shields.io/badge/SAP%20CAP-db8b0b?style=for-the-badge&logo=sap&logoColor=white 
[CAP-url]: https://cap.cloud.sap/docs/
[Postgresql]: https://img.shields.io/badge/PostgreSQL%20on%20SAP%20BTP-4169E1?style=for-the-badge&logo=postgresql&logoColor=white
[Postgresql-url]: https://discovery-center.cloud.sap/serviceCatalog/postgresql-hyperscaler-option?region=all