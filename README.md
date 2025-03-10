# Opin Kerfi - Ansible Uppskriftir fyrir Windows

## Uppskriftir

* setja_inn_windows_upfaerslur.yml - Setur inn allar CriticalUpdates, SecurityUpdates og endirræsir eftir þörfum.
* pingtest.yml - Framkvæmir pingprófun

## Undirbúningur á windows vél

Á vélinni sem á að stýra með Ansible opnið Windows PowerShell ISE og keyrið eftirfarandi:

```powershell
$url = "https://raw.githubusercontent.com/opinkerfi/ok-ansible-windows/master/powershell_scripts/ConfigureRemotingForAnsible.ps1"
$file = "$env:temp\ConfigureRemotingForAnsible.ps1"

(New-Object -TypeName System.Net.WebClient).DownloadFile($url, $file)

powershell.exe -ExecutionPolicy ByPass -File $file
```

Það sem þessi skrifta gerir er að sækja ```ConfigureRemoteForAnsible.ps1```skrituna sem stillir ```winrm``` af og opnar eldvegg fyrir winrm tengingar. 

__ATH:__ Ef stýrikerfið er 2008 eða windows 7 þarf að uppfæra powershell og .net framework sbr.  https://docs.ansible.com/ansible/latest/user_guide/windows_setup.html#upgrading-powershell-and-net-framework

## Tips and Tricks

### Þróun á ansible módúlum 
__Sjá:__ https://docs.ansible.com/ansible/latest/dev_guide/developing_modules_general_windows.html

### Hjáleið vegna python bug með vagrant á osx

Export-a út eftifarandi breytu svo ansible keyri winrm aðgerðir án þess að stoppa.

```export OBJC_DISABLE_INITIALIZE_FORK_SAFETY=YES```
