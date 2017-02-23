# Puma Jungle Configurations for JumpStart Servers
[Puma](https://github.com/puma/puma) is a Rails server that we use on our servers. Puma comes with a tool called [Puma Jungle](https://github.com/puma/puma/tree/master/tools/jungle/init.d) that will automatically start all Rails applications that use Puma when the server restarts.

Unfortunately, due to the way we setup the applications on the servers, a couple changes are needed to the Puma Jungle configuration files. Below is a description of the changes and how to setup the server.

# The Changes
* In the original config files, `bundle exec` is used from the application root directory which is not correct. The application current directory is the correct directory to use. So the `cd` statement before the `bundle exec` has been updated to use the current folder. Both puma and run-puma files have been updated with this fix.
* Our [Rails Starter Template](https://github.com/JumpStartGeorgia/Starter-Template) comes with tasks to manage the Puma Jungle such as start, stop, add, etc. The stop and status commands use bundle exec and in order for these commands to work, the application user from the config file must be included as part of the bundle exec commands. This only effects the puma file.

# How to Setup the Server
Follow the instructions to install the [Puma Jungle](https://github.com/puma/puma/tree/master/tools/jungle/init.d), but instead of using the puma and run-puma files from that repo, use the ones here.

