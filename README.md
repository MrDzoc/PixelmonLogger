# PixelmonLogger
Admin plugin for Pixelmon that logs various player actions

#### Commands

Command | Description | Permission
--------| ------------| ----------
/pl view \<type> [pokemon] [time] | Views logs for the specified type. | pixellogger.logs.all
/pl player \<player> [type] [pokemon] [time] | Views logs for the specified player. | pixellogger.logs.player
/pl clear | Deletes all logs in the database. | pixellogger.clear
/pl reload | Reloads the config file. | pixellogger.reload

- Logs default to a time of 1 day, so doing "/pl v all" would get every log from the past 1 day
- You can do "/pl v GTS all 100" to get every log for the GTS from the past 100 days
- "/pl v m1zark all Abra 10" would show every log for that player involving Abra in the past 10 days

#### Config

From the config you can enable/disable exactly what you want to be logged.

```hocon
General {
    Logging {
        enableGTSLogging=false
        enableMegaDrops=false
        enableNormalCatching=false
        enablePixelExtrasLogging=false
        enablePokeLoot=false
        enableReceivedLogging=true
        enableReleaseLogging=true
        enableSafeTradeLogging=false
        enableShinyLegendary=true
        enableTradeLogging=true
        enableWTLogging=false
    }
    # Time, in days, to automatically remove logs
    removeExpired=30
}
Storage {
    MySQL {
        Password=
        URL="[host]:[port]/[database]"
        Username=
    }
    # Types: h2, mysql
    storageType=h2
}
```

