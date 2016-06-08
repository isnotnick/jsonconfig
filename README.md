# jsonconfig

This is a Go package to parse a configuration file in JSON.

Usage
Write your config file as a JSON object. For example:

{
        "host_and_port": ":9556",
        "environment": "production",
        "priority_level": 20,
        "alert_recipients": ["patrick", "gus"]
}
Load the config file:

config := jconfig.LoadConfig("/etc/super.conf")
Get some values out of it:

if config.GetString("environment") == "production" {
    // ...
}
sender := NewSender(config.GetInt("priority_level"))
sender.Recipients = config.GetArray("alert_recipients")
