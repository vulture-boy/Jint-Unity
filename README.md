# Jint Unity
  
Jint Unity allows the installation of [Jint](https://github.com/sebastienros/jint) through the package manager, allowing you to execute JavaScript in Unity. This was originally forked from [Magicblock's repository](https://github.com/magicblock-labs/Jint-Unity) which has a copyright license claim. However, the functional content, aside from the sample, isn't valid to claim for copyright; I've removed the sample content to lift the licensing restrictions.

Essentially all this repository does is connect the .dll available from Jint's repository with a `package.json` so that Unity can import it via the package manager. It targets NET Standard 2.1 for compatability with Unity 2019 and above.

## Installation

* Open [Unity Package Manager](https://docs.unity3d.com/Manual/upm-ui.html) window.
* Click the add **+** button in the status bar; the options for adding packages appear.
* Select Add package from git URL from the add menu. A text box and an Add button appear.
* Enter the `https://github.com/vulture-boy/Jint-Unity.git` Git URL in the text box and click Add (you can append the version number to target [a specific release version](https://github.com/vulture-boy/Jint-Unityreleases), if available).
  
## Usage

### Example 1

```csharp
var square = new Engine()
    .SetValue("x", 3) // define a new variable
    .Evaluate("x * x") // evaluate a statement
    .ToObject();
Debug.Log(square);
```

### Example 2

```csharp
Engine js = new Engine();
js.SetValue("Console",typeof(Debug));
js.Execute("function Compute() { const a = 3; const res = a * a; Console.Log('Js computation: ' + res); }");
js.Invoke("Compute");
```

### Example 3

Loading a script: 

```csharp
var source = new StreamReader(Application.dataPath + "/Resources/" + "main.js");
string script = source.ReadToEnd();
source.Close();
js.Execute(script);

```