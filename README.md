# PixelmonLogger
This is an Sponge plugin for Pixelmon that logs various player actions. It will create a detailed log of the action, date, and Pokemon for each event.

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
- "all" can be used for [Pokemon] and [Type] to retreive all types/pokemon

#### Additional Permissions
- pixellogger.delete -> Delete individual logs
- pixellogger.collect -> Allows you to click on a Pokemon and have it sent to your storage.

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
- PixelExtras logging will track uses of /pokegift and all its aliases
- If you are using Simons WT, you need to disable the WT logging option as his will get tracked via the Received and Released logging.
- Received logging will log everything that comes in from a command, like pokegive or as mentioned Simons WT.
- Released logging will log deleting a Pokemon via the PC, as well as any command that removes a Pokemon/uses the right event.
- PokeLoot logging will log whenever a player opens a pokeloot, as well as the locationa and type it was.
- Shiny/Legendary logging will log when a players captures a shiny or legendary... likewise normal logging will log every normal Pokemon capture.
- MegaDrops logging will log when a player kills a Mega Boss as well as all items they received from said boss.
