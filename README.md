# Packet Utils

This repository contains an API for working with Packets in Old School RuneScape. When new revisions of RuneLite or the OSRS
client are released this repo will need to be synced with its upstream and in the bootstrap file for Kraken Plugin. 
To sync perform the following steps:

- (One time only): `git remote add upstream https://github.com/Ethan-Vann/PacketUtils.git`
- Sync with master: `git pull upstream master`
- Run a build to ensure everything compiles: `./gradlew clean :FatJar`
- Commit and push synced changes: `git commit -m "chore: sync with upstream master"; git push`
- GitHub Workflows will build the artifact and publish to MinIO bumping the version based on the build number
  - Ensure this workflow completed successfully
- (Automated) Ensure when the `bootstrap.json` file is generated in the Kraken Plugins repository that it uses the latest version of `packet-utils` in MinIO.

It can be included in any Gradle projects which use [JitPack.io](https://jitpack.io) like so:

```groovy
def version = 'x.y.z'

dependencies {
    // ...
    implementation group: 'com.github.cbartram', name:'packet-utils', version: version
}
```
