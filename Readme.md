<p align="center">
<img src="192x192.png">
</p>

### About Auto8 DevOps
Our mission is to simplify complex processes and enhance productivity
by automating tedious tasks associated with server management,
software installation, backups, and database operations.

<p align="center">
<img src="app.png">
</p>

#### Installation

Some basic requirements for Auto8 DevOps.
- MacOS
- HomeBrew (/usr/local/bin/brew) for Redis status check
- Anisble, and Ansible Playbook (~/Library/Python/3.9/bin/ansible-playbook) for deploying plays

After you have Redis, and Ansible please visit the `docs` and you should see checkmarks after a few seconds.
We have a template for host, and a few plays already created with empty variables.

If you have feature or issues please add them here :).

#### MacOS Release Process

Auto8 DevOps release process.

1. Add missing certificates to the `./builds` folder:
   -  Auto8PPN.provisionprofile
   -  CertificateSigningRequest.certSigningRequest
   -  developerID_application.cer
2. Make sure the certificate are valid by running `npm run build:mac`
   -  If all goes well this will not throw any error o/w proceed with caution
      and follow the error stack.
3. Update package.json with correct `version`
4. Perform the following set of command:

   ```
   npm run clean
   npm run build:mac

   # ONE TIME command
   xcrun notarytool store-credentials --apple-id "XXX@gmail.com" --team-id "XXX"

   xcrun notarytool submit XXX.zip --keychain-profile "devops.auto8.app" --wait
   ```
