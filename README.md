# OSC OnDemand Dashboard

This app is a PUN based Rails app for Open OnDemand that serves as a gateway to launching other Open OnDemand apps.

## Install

This Rails app doesn't use a database.

```
scl enable nodejs010 rh-ruby22 git19 bash

cd /path/to/build/directory/sys
git clone clone git@github.com:OSC/ood-ondemand.git dashboard
cd dashboard
git checkout v1.0.3 # latest version
bin/bundle install --path vendor/bundle
```

At this point, configure the app and its branding by copying .env to .env.local and modifying the values of the environment variables. See below for details on configuration and branding.

After updating the .env.local file, build the assets to complete the installation:

```
RAILS_ENV=production bin/rake assets:precompile # make sure that RAILS_RELATIVE_URL_ROOT is unset before running this command
bin/rake tmp:clear
```

At this point, you should copy the directory to the deployment directory, if that location is not the same place as the build directory. For more explanation of how this is done, see https://github.com/OSC/Open-OnDemand#app-deployment-strategy.

When updating a deployed version of the Open OnDemand dashboard: 

1. do a git fetch
2. checkout the latest tag
3. rebuild the assets
4. clear the cache and touch the tmp/restart.txt file so Passenger reloads the app

## Configuration

Configuration is done within the .env file. 
Look at the .env file to see an example configuration for OSC.


## Branding

Branding is done within the .env file. Bootstrap variables are overridden using OodAppkit (https://github.com/OSC/ood_appkit#override-bootstrap-variables).

Look at the .env file to see example branding for OSC.
