#  IniFileStream - INI File Parser for .NET
An INI file parser for .NET. Provides the `IniFileStream` class to read and write INI files without the use of P/invoke. 


## Samples

### Read keys from a specific section:
```csharp
try
{
    var ini = new IniFileStream("config.ini");
    
    foreach (var key in ini.GetKeysFromSection("TestApplication"))
    {
        switch (key.Key)
        {
            case "Width":
                Width = int.Parse(key.Value);
                break;
            case "Height":
                Height = int.Parse(key.Value);
                break;
            case "Text":
                Text = key.Value;
                break;
        }
    }
}
catch (Exception e)
{
    Debug.WriteLine(e.Message);
}
```

### Read all keys from all sections:
```csharp
try
{
    var ini = new IniFileStream("config.ini");
    
    foreach(var section in ini.Sections)
    {
        foreach (var key in ini.GetKeysFromSection(section))
            Debug.WriteLine($"{key.Key}={key.Value}");
    }
}
catch(Exception e)
{
    Debug.WriteLine(e.Message);
}
```
