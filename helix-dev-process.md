
@kptdobe and I brainstormed how a typical Helix project would be kicked off and moved through the process from dev to publish (and back). Here are the different stages we came up with, mapped to `helix-cli` commands we expect to be used and problems experienced. The goal of this discussion is to agree on the use cases, so we can: 
* think about how to streamline moving between stages for developers
* write e2e test cases
* simplify the `helix-ci` code?

**Stage** | **Use Case** | **Commands** | **How to get to this stage** | **Documentation** | **Projects** | **Issues**
--------- | ------------ | ------------ | ---------------------------- | ----------------- | ------------ | ----------
**1. Project kickoff** | Developer starts playing around with Helix. Code and content are local. | [x] up<br>[x] build<br>~~[ ] deploy~~<br>~~[ ] publish~~ | Run `hlx demo` | - [Getting Started Guide](https://github.com/adobe/project-helix/blob/master/getting-started.md)<br>- [Helix in 60 seconds](https://github.com/adobe/project-helix/blob/master/start-developing-your-first-helix-project-in-60-seconds.md) |  | `deploy` & `publish` are not possible and should fail gracefully
**2. Configure GitHub repo** | Developer points Helix to their GitHub repo. | [x] up<br>[x] build<br>[ ] deploy<br>[ ] publish | Use `git remote add origin` | - [Getting Started Guide](https://github.com/adobe/project-helix/blob/master/getting-started.md) | - [www.project-helix.io](https://github.com/adobe/project-helix.io) | `deploy` & `publish` are expected to work, but currently fail:<br>- #000<br>- #000<br>- ...
**3. Separate code & content repos** | Developer defines a dedicated remote GitHub repo for the content | [x] up<br>[x] build<br>[ ] deploy<br>[ ] publish | Add `content` property in `helix-config.yaml` (optionally add `code`) | - [Getting Started Guide](https://github.com/adobe/project-helix/blob/master/getting-started.md) | - [Adobe-Developer-Site](https://github.com/adobe/Adobe-Developer-Site)<br>- [helix-helpx](https://github.com/adobe/helix-helpx) | `deploy` & `publish` are expected to work, but currently fail:<br>- #000

