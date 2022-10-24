#  INI File Parser for .NET
An INI file parser for .NET that provides the `IniFile` class to read and write INI files without the use of P/invoke. This class allows you to easily integrate basic INI configuration files into your application.
 

## Samples

### 1. Read keys from a specific section
```csharp
try
{
    var ini = new IniFile("config.ini");
    
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

### 2. Read all keys from all sections
```csharp
try
{
    var ini = new IniFile("config.ini");
    
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
