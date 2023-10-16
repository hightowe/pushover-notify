# pushover-notify
A simple command-line [Pushover.net](https://pushover.net) notifier script, written in Perl

## Usage ##
~~~
$ pushover-notify --help
Usage: pushover-notify --user=<user-key> --token=<token> --msg <message>

  --user=s       The Pushover user to message.
  --token=s      The Pushover API token to use.
  --msg=s        The message to send.
  --sound=s      The sound to use. See https://pushover.net/api#sounds
  --priority=i   The message priority (-2..2). See https://pushover.net/api#priority
  --quiet        Don't write the "Success" message on success.
  --help         This message.
~~~

### Examples ###
#### Command line ####
~~~
$ pushover-notify --user pushover_user --token pushover_token --msg Message from Pushover" --sound intermission --priority 1
Success
~~~

#### Within a cron job ####
~~~
$ crontab -l|grep mailq
# Monitor for the mailq backing up on this host
3 */2 * * * [ "$(mailq | grep -c -E -i '^[a-z0-9]+')" -lt 5 ] || pushover-notify --user pushover_user --token pushover_token --priority 2 --sound intermission --quiet --msg "[$(hostname)] mailq is over the limit"
~~~
