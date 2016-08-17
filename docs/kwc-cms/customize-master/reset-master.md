#RESET MASTER.TPL FOR A SPECIFIC PAGE IN WEB

If you want to completely change the Master.tpl just add a Master.tpl file to your component. This should replace the Root/Master.tpl and provide the new one for every subpage.

Also set

`$ret['flags']['resetMaster'] = true;`