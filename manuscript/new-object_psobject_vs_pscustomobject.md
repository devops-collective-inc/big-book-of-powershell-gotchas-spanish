# New-Object PSObject vs. PSCustomObject
A menudo hay cierta confusión en lo que respecta a las diferencias entre el uso de nuevo objeto PSObject y PSCustomObject, así como el funcionamiento de ambos.

Cualquiera de los dos se puede utilizar para formar un conjunto de valores en una colección de objetos PowerShell y agruparlos en una sola entidad. Asimismo, ambas formas darán salida a los datos como NoteProperties en los tipos de objeto System.Management.Automation.PSCustomObject. Así que ¿cuál es la gran diferencia entre ellos?

Para empezar, el Cmdlet New-Object fue introducido en PowerShell v1.0 y ha pasado por una serie de cambios, mientras que el uso de la clase PSCustomObject vino más tarde en la versión 3.0. Para los sistemas que utilicen PowerShell v2.0 o anterior, se debe utilizar New-Object. La diferencia clave entre la versión 2.0 y la versión 1.0 desde un punto de vista administrativo es que 2.0 permite el uso de tablas hash. Por ejemplo:

## New-Object PSObject en v1.0

```
$Path = "c:\scripts"
$Directory = Get-Acl -Path $Path

ForEach ($Dir in $Directory.Access){

    $DirPermissions = New-Object -TypeName PSObject
    $DirPermissions | Add-Member -MemberType NoteProperty -Name Path -Value $Path
    $DirPermissions | Add-Member -MemberType NoteProperty -Name Owner -Value $Directory.Owner
    $DirPermissions | Add-Member -MemberType NoteProperty -Name Group -Value $Dir.IdentityReference
    $DirPermissions | Add-Member -MemberType NoteProperty -Name AccessType -Value $Dir.AccessControlType
    $DirPermissions | Add-Member -MemberType NoteProperty -Name Rights -Value $Dir.FileSystemRights

    $DirPermissions
}
```

Con el método New-Object en PowerShell v1.0, tiene que declarar el tipo de objeto que desea crear y agregar miembros a la colección en comandos de forma individual. Sin embargo en la versión 2.0 con la capacidad de utilizar hashtables:

## New-Object en PS 2.0

```
$Path = "c:\scripts"
$Directory = Get-Acl -Path $Path

ForEach ($Dir in $Directory.Access){

    $DirPermissions = New-Object -TypeName PSObject -Property @{

    'Path' = $Path
    'Owner' = $Directory.Owner
    'Group' = $Dir.IdentityReference
    'AccessType' = $Dir.AccessControlType
    'Rights' = $Dir.FileSystemRights

    }

    $DirPermissions
}
```

Aquí está la salida:

![Note theorder of output vs. order in the hash table](images/PSObject1.jpg)

Esta forma nos ahorra una gran cantidad de escritura al mismo tiempo que permite un script más limpio. Sin embargo ambos métodos tienen el mismo problema. La salida no está necesariamente en el mismo orden en que se ha declarado, así que si está buscando un formato determinado, puede que no funcione. PSCustomObject corrigió esto cuando fue introducido en la versión 3.0.

## PSCustomObject en PowerShell v3.0
```
$Path = "c:\scripts"
$Directory = Get-Acl -Path $Path

ForEach ($Dir in $Directory.Access){
    [PSCustomObject]@{
    Path = $Path
    Owner = $Directory.Owner
    Group = $Dir.IdentityReference
    AccessType = $Dir.AccessControlType
    Rights = $Dir.FileSystemRights
    }#EndPSCustomObject
}#EndForEach
```

![Note the order of the properties](images/PSObject2.jpg)

Como se puede observar, la salida siempre coincidirá con lo que se ha definido en el Hashtable. Otra ventaja de usar PSCustomObject es que la enumeración de los datos se hace más rápidamente que su contraparte New-Object. Lo único que debe tener en cuenta con PSCustomObject es que no funcionará con los sistemas que ejecutan PowerShell  v2.0 o anteriores.




