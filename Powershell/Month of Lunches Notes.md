##Help##

{
    Help *Common*
    CommonParameters
    - DEBUG (db)
    - ERRORACTION (ea)
    - ERRORVARIABLE (ev)
    - INFORMATIONACTION (infa)
    - INFORMATIONVARIABLE (iv)
    - OUTVARIABLE (ov)
    - OUTBUFFER (ob)
    - PIPELINEVARIABLE (pv)
    - VERBOSE (vb)
    - WARNINGACTION (wa)
    - WARNINGVARIABLE (wv)

    ACTION param:
    Name               Value
    ------------------ ------ -
    Suspend            5
    Ignore             4
    Inquire            3
    Continue           2
    Stop               1
    SilentlyContinue   0

    --

    About topics in help
    Help about*
    lists all

    --

    Update-help (manual)
    Help Get-EventLog -online (retrieve web based)

    --

    -ShowWindow (pop up local help)

    --

    Lab:
    Update-Help
    Help Converto-html
    Help Out-file
    Help *processes* (13 results) /get-command -noun Process
    Help Write-EventLog
    Help New-alias/export-alias/import-alias/set-alias 
    Get-Help transcript
    Help start-transcript
    Help Event
    Limit-EventLog
    Help Service
    Get-Service
    Get-Help Out-file -detailed
    80 character default width
    `$PSDefaultParameterValues['out-file:width'] = 2000` before using `Out-File`.
    NOClobber - prevent overwrite
    Get-Help alias
    Get-Process | Where-Object { $_.WorkingSet -gt 20000000 }
    About_arrays

    -parameter computername
    -parameter newest
}

##Commands, not scripts##

{
    Commands, get bored, chuck in note, add .ps1, script exist 

}

{
4.2
    Basic anatomy:Full form syntax

Command         parameter1          parameter2                  parameter3
Get-eventlog    -logName Security   -ComputerName WIN8,SERVER1  -Verbose

The cmdlet name is Get-EventLog. PowerShell cmdlets always have this verb-noun naming format. We explain more about cmdlets in the next section.
The first parameter name is -LogName, and it’s being given the value Security. Because the value doesn’t contain any spaces or punctuation, it doesn’t need to be in quotation marks.
The second parameter name is -ComputerName, and it’s being given two values: WIN8 and SERVER1. These are in a comma-separated list, and because neither value contains spaces or punctuation, neither value needs to be inside quotation marks.
The final parameter, -Verbose, is a switch parameter. That means it doesn’t get a value; specifying the parameter is sufficient.
Note that there’s a mandatory space between the command name and the first parameter.
Parameter names always start with a dash (-).
There’s a mandatory space after the parameter name, and between the parameter’s value and the next parameter name.
There’s no space between the dash (-) that precedes a parameter name and the parameter name itself.
Nothing here is case-sensitive.


    A cmdlet is a native PowerShell command-line utility. These exist only inside PowerShell and are written in a .NET Framework language such as C#. The word cmdlet is unique to PowerShell, so if you add it to your search keywords on Google or Bing, the results you get back will be mainly PowerShell-related. The word is pronounced command-let.
    A function can be similar to a cmdlet, but rather than being written in a .NET language, functions are written in PowerShell’s own scripting language.
    A workflow is a special kind of function that ties into PowerShell’s workflow execution system.
    An application is any kind of external executable, including command-line utilities such as Ping and Ipconfig.
    Command is the generic term that we use to refer to any or all of the preceding terms.

Names start with verb: Get-Verb

--

Use Aliases: get-alias -Definition "Get-Service" = gsv -> Get-Service

Can create own alias's - New-Alias - need to export and import

Shortcuts: ComputerName= -compu

Parameters have aliases too: COmputername = cn 

(get-command get-eventlog | select -ExpandProperty parameters)
     .computername.aliases


Positional parameters are shown in help in [parameter] square brackets. [[parameter] something]

help -full for info 

Cheating.... Show-Command <--------------- :D 
    Can copy output and save.
    Only works with single Commands

Placeholders: $something

--% pass to cmd 




}