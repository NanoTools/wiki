Note: `amount` values should always be in RAW.

# Send to an address

    xrb:xrb_<encoded address>[?][amount=<raw amount>][&][label=<label>][&][message=<message>]

Just the address

    xrb:xrb_3wm37qz19zhei7nzscjcopbrbnnachs4p1gnwo5oroi3qonw6inwgoeuufdp

Address and an amount (as RAW)

    xrb:xrb_3wm37qz19zhei7nzscjcopbrbnnachs4p1gnwo5oroi3qonw6inwgoeuufdp?amount=1000

Address and a label

    xrb:xrb_3wm37qz19zhei7nzscjcopbrbnnachs4p1gnwo5oroi3qonw6inwgoeuufdp?label=Developers%20Fund%20Address

Send to an address with amount, label and message

    xrb:xrb_3wm37qz19zhei7nzscjcopbrbnnachs4p1gnwo5oroi3qonw6inwgoeuufdp?amount=10&label=Developers%20Fund&message=Donate%20Now

# Private Key Import

    xrbkey:<encoded private key>[?][label=<label>][&][message=<message>]

# Seed Import

    xrbseed:<encoded seed>[?][label=<label>][&][message=<message>][&][lastindex=<index>]