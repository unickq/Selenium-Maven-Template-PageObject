Selenium-Maven-Template-PageObject
=======================

Forked from [Selenium-Maven-Template by Ardesco](https://github.com/Ardesco/Selenium-Maven-Template).

### Page Object
Tests looks like:
```
        GooglePage googlePage = new GooglePage();
        googlePage.navigate();
        googlePage.performSearch("Milk!");
        googlePage.waitUntilResultsLoaded("Milk");
        googlePage.getValidator().assertThatTitleContains("Milk");
```

#####Page object implementation:
* Assertions methods for pages are located in Validator classes.
* WebElements for pages are located in Map classes.
* Pages behaviour described in Page classes.

Modified tests could be fount at GoogleExamplePageObjectIT class.

_P.S. Used selenium 3.0.0beta3 with Chrome because of unstable work with FF_
### Original Description

[![Join the chat at https://gitter.im/Ardesco/Selenium-Maven-Template](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/Ardesco/Selenium-Maven-Template?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

A maven template for Selenium that has the latest dependencies so that you can just check out and start writing tests in four easy steps.  If you like what you see have a look at my Selenium book [Mastering Selenium Webdriver](https://www.amazon.co.uk/Mastering-Selenium-WebDriver-Mark-Collin/dp/1784394351).


1. Open a terminal window/command prompt
2. Clone this project.
3. `cd Selenium-Maven-Template` (Or whatever folder you cloned it into)
4. `mvn clean verify`

All dependencies should now be downloaded and the example google cheese test will have run successfully (Assuming you have Firefox installed in the default location)

### What should I know?

- To run any unit tests that test your Selenium framework you just need to ensure that all unit test file names end, or start with "test" and they will be run as part of the build.
- The maven failsafe plugin has been used to create a profile with the id "selenium-tests".  This is active by default, but if you want to perform a build without running your selenium tests you can disable it using:

        mvn clean verify -P-selenium-tests
        
- The maven-failsafe-plugin will pick up any files that end in IT by default.  You can customise this is you would prefer to use a custom identifier for your Selenium tests.

### Anything else?

Yes you can specify which browser to use by using one of the following switches:

- -Dbrowser=firefox
- -Dbrowser=chrome
- -Dbrowser=ie
- -Dbrowser=edge
- -Dbrowser=opera
- -Dbrowser=htmlunit
- -Dbrowser=phantomjs

You don't need to worry about downloading the IEDriverServer, MicrosoftWebDriver, chromedriver , operachromium, or wires binaries, this project will do that for you automatically.

Not got PhantomJS?  Don't worry that will be automatically downloaded for you as well!

You can specify a grid to connect to where you can choose your browser, browser version and platform:

- -Dremote=true 
- -DseleniumGridURL=http://{username}:{accessKey}@ondemand.saucelabs.com:80/wd/hub 
- -Dplatform=xp 
- -Dbrowser=firefox 
- -DbrowserVersion=44

You can even specify multiple threads (you can do it on a grid as well!):

- -Dthreads=2

You can also specify a proxy to use

- -DproxyEnabled=true
- -DproxyHost=localhost
- -DproxyPort=8080

If the tests fail screenshots will be saved in ${project.basedir}/target/screenshots

If you need to force a binary overwrite you can do:

- -Doverwrite.binaries=true

### It's not working!!!

You have probably got outdated driver binaries, by default they are not overwritten if they already exist to speed things up.  You have two options:

- `mvn clean verify -Doverwrite.binaries=true`
- Delete the `selenium_standalone_binaries` folder in your resources directory