Let's grab the Ojbect ID of the group we want to add people to, To do so let's look into the overview of the group
![image](https://user-images.githubusercontent.com/44326428/126912613-9d6aded6-5129-4822-af07-e3f14f063c27.png)

lets do a filter for people we want, in this example I'm running people that are not in China nor USA and those will be considered in Europe, your case will vary so do it accordingly. At the same time I will add them in to a variable that will hold them as an array

```
$europe = Get-AzureADUser | Where-Object {$_.country -ne "usa" -and $_.country -ne "china" }
```

Now that we have both values, let's add them into the final script.

``` Ruby
$europe = Get-AzureADUser | Where-Object {$_.country -ne "usa" -and $_.country -ne "china" }
foreach ($user in $europe){
    Add-AzureADGroupMember -ObjectId "d9190e02-4695-40f4-841c-7d9497c013be" -RefObjectId $user.objectid
}
```

Now regardless of your Powershell 5.1 or 7.1.3 you will get an error but its bening, and this is the reason why I'm writing the script, to help others minimize the time in researching.

![image](https://user-images.githubusercontent.com/44326428/126912854-614e698e-68d2-47c0-a8e5-b4ab61fdf423.png)




