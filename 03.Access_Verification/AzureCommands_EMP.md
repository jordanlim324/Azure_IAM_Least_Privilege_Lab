## Test 1: Creating/Writing Tag (Expected: Success)

**Command:**
```powershell
PS C:\Users\WDAGUtilityAccount>az tag create  --resource-id /subscriptions/<MySubscriptionId>/resourceGroups/Shirabuki_Corporation --tags TestTag=EmployeeVerification
```
Result: Success

Output:
```
{
  "id": "/subscriptions/<MySubscriptionId>/resourceGroups/Shirabuki_Corporation/providers/Microsoft.Resources/tags/default",
  "name": "default",
  "properties": {
    "tags": {
      "TestTag2": "Employee2Verification"
    }
  },
  "resourceGroup": "Shirabuki_Corporation",
  "type": "Microsoft.Resources/tags"
}
```

## Test 2: Deleting Resource Group (Expected: Fail/Forbidden)

**Command:**
```powershell
PS C:\Users\WDAGUtilityAccount>az group delete --name Shirabuki_Corporation --y
```
Result: Denied

Output:
```
(AuthorizationFailed) The client 'Shirabuki_Emp_2@<MyTenant>.onmicrosoft.com' with object id '6643889d-e652-40f1-9d1f-8fa70996a03f' does not have authorization to perform action 'Microsoft.Resources/subscriptions/resourcegroups/delete' over scope '/subscriptions/<MySubscriptionId>/resourcegroups/Shirabuki_Corporation' or the scope is invalid. If access was recently granted, please refresh your credentials.
Code: AuthorizationFailed
Message: The client 'Shirabuki_Emp_2@<MyTenant>.onmicrosoft.com' with object id '6643889d-e652-40f1-9d1f-8fa70996a03f' does not have authorization to perform action 'Microsoft.Resources/subscriptions/resourcegroups/delete' over scope '/subscriptions/<MySubscriptionId>/resourcegroups/Shirabuki_Corporation' or the scope is invalid. If access was recently granted, please refresh your credentials.
```