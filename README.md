## Unity Coding Style Guide

This document outlines the coding style and conventions to be followed in Unity C# projects to ensure consistency, readability, and maintainability across the codebase.

---

### 🏷️ Versioning Convention

Version numbers should follow the `A.B.C[-tag[.N]]` format:

- `A` (Major): Breaking or structural changes.
- `B` (Minor): Feature additions or behavioral adjustments.
- `C` (Patch): Bug fixes and small improvements.
- `-tag`: (Optional) Pre-release identifier such as `alpha`, `beta`, `rc`.
- `.N`: (Optional) Incremental number for pre-release builds.

Examples:
- `1.0.0-alpha` – first alpha release
- `1.0.0-beta.2` – second beta version
- `2.0.0-rc.1` – first release candidate
- `2.0.0` – stable production release

Guidelines:
- Increment `A` for breaking changes or major shifts in logic.
- Increment `B` for new features or behavioral adjustments.
- Increment `C` for small fixes or polish.
- Use `-tag` identifiers for internal testing, QA, or experimental versions before official release.
- All commits or deployments should be associated with a clear version tag.

---

### 📝 Naming Conventions

```csharp
// Classes & Structs: PascalCase
class GameManager {}
class PlayerController {}

// Methods: PascalCase
void StartGame() {}
void ResetTimer() {}

// Variables:
private int _exampleValue;       // private fields: _camelCase
public int Health { get; set; }  // public properties: PascalCase
const int MAX_VALUE = 100;       // constants: ALL_CAPS

// Serialized/private inspector-visible/public-inspector fields:
[SerializeField] private GameObject target; // no underscore for inspector-visible fields
public float moveSpeed;                      // same rule for public inspector fields

// Interfaces: Prefix with 'I'
interface IDamageable {}
interface IMoveable {}

// Enums: PascalCase for enum names and values
enum PlayerState { Idle, Running, Jumping }
```

### ⚙️ Code Formatting

```csharp
// Use 4 spaces for indentation
// Always use braces {}
// Opening braces on a new line
// Keep methods under 40 lines when possible

if (isActive)
{
    DoSomething();
}
```

### 📦 Script Template

```csharp
using UnityEngine;

public class ExampleScript : MonoBehaviour
{
    [SerializeField] private int exampleValue = 0;

    private void Awake()
    {
        // Initialization
    }

    private void Start()
    {
        // Start logic
    }

    private void Update()
    {
        // Frame update logic
    }
}
```

### 🧪 Comments & Documentation

* All comments should be written in **English**.

```csharp
/// <summary>
/// Handles player health regeneration.
/// </summary>
public void RegenerateHealth()
{
    // Increase health based on regen rate
}
```

* Use inline comments sparingly and only when the logic is not obvious.

### 🔗 Unity-Specific Practices

```csharp
// Use SerializeField instead of public fields
[SerializeField] private GameObject target;

// Cache references in Awake or Start
private Rigidbody _rb;
private void Awake()
{
    _rb = GetComponent<Rigidbody>();
}

// Avoid calling GetComponent in Update
// Avoid GameObject.Find in production

// Prefer TryGetComponent when unsure if component exists
if (TryGetComponent(out Rigidbody rb))
{
    rb.AddForce(Vector3.up);
}
```

### ✅ Best Practices

```csharp
// Use nameof instead of string literals
Debug.Log(nameof(GameManager));

// Avoid magic numbers
private const float Gravity = 9.81f;

// Use explicit private modifier
private int _score;

// Split large classes when needed
// Use partials or separate files

// Mindful use of coroutines and async
StartCoroutine(LoadSceneAsync());
```

---

Maintaining a consistent style helps everyone on the team read, write, and debug code more efficiently. This guide is a living document and should evolve with project needs.
