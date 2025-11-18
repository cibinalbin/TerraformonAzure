

```hcl
resource "azurerm_storage_account" "sa" {
  name                     = "mytfstatestorage1234" #Ensure globally unique name
  resource_group_name      = "Sirin-RG" #Ensure Your RG  
  location                 = "East US"
  account_tier             = "Standard"
  account_replication_type = "LRS"
  
  blob_properties {
    versioning_enabled = true
  }
}

resource "azurerm_storage_container" "container" {
  name                  = "tfstate-container"
  storage_account_id    = azurerm_storage_account.sa.id
  container_access_type = "private"
}
```
