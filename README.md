# npm ci vs npm install

## Diff

_It compares only for building._<br/>
_It doesn't count like `npm install` can be used for installing a package_

| npx ci                                                 | npm install                                                                                                                  |
| ------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------- |
| Install packages from package.json                     | Install packages from package-lock.json                                                                                      |
| It may writes package-lock.json                        | It never writes package.json or package-lock.json                                                                            |
| It's slower in execution                               | It's faster in execution because It just install dependencies from package-lock.json and throw an error if there's a problem |
| If there is a node_modules, It doesn't change anything | If there is a node_modules, It removes it before installing                                                                  |
| It used for updating the list of dependencies          | It used for the deterministic build                                                                                          |

If you're sure that you've updated pakcage-lock.json before deploying (It can be updated well by just `npm install`).<br />
So then, just use `npx ci` for fast build. and if you've done to test the project with the dependencies, There are no worries for side effects of the denpendencies (If the packages will be installed well).<br /><br />
_Plus+_ `npm ci` will delete a _node_modules_ If there is, so add the _node_modules_ in a ignore list for removing wasted time.
