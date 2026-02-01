# VEGAS Pro Scripting: Common Pitfalls and Safety Checks

Quick reference guide for avoiding common regression-causing mistakes in VEGAS Pro 23 scripts.

---

## Critical Safety Checks (ALWAYS Include)

### 1. Project State Validation
```
ALWAYS check:
- Is a project open?
- Is the project null?
- Can we access Vegas.Project?
```

### 2. Selection Validation
```
Before using selected items:
- Check if selection exists
- Check if selection is empty
- Verify selection type matches expected type
- Handle null selections gracefully
```

### 3. File Operations
```
Before any file operation:
- Check if file/directory exists
- Check if path is valid
- Check write permissions
- Check available disk space (for large operations)
- Use try-catch with proper cleanup
```

### 4. Error Handling
```
NEVER:
- Let exceptions bubble up silently
- Modify files without backups
- Leave project in inconsistent state on error

ALWAYS:
- Show user-friendly error messages
- Log errors for debugging
- Clean up partial changes on failure
- Provide recovery options
```

---

## Common Breaking Change Patterns

### Pattern 1: Null Reference Errors
**Problem**: Assuming objects exist without checking

**BEFORE (Unsafe)**:
```csharp
var track = Vegas.Project.Tracks[0];  // Crashes if no tracks
track.Events[0].Length = 5;           // Crashes if no events
```

**AFTER (Safe)**:
```csharp
if (Vegas.Project == null || Vegas.Project.Tracks.Count == 0) {
    MessageBox.Show("No tracks found.");
    return;
}
var track = Vegas.Project.Tracks[0];
if (track.Events.Count == 0) {
    MessageBox.Show("No events on track.");
    return;
}
track.Events[0].Length = 5;
```

### Pattern 2: Index Out of Range
**Problem**: Using indexes without bounds checking

**BEFORE (Unsafe)**:
```csharp
var event = track.Events[eventIndex];
```

**AFTER (Safe)**:
```csharp
if (eventIndex < 0 || eventIndex >= track.Events.Count) {
    MessageBox.Show($"Invalid event index: {eventIndex}");
    return;
}
var event = track.Events[eventIndex];
```

### Pattern 3: File Path Assumptions
**Problem**: Hardcoded or unvalidated paths

**BEFORE (Unsafe)**:
```csharp
string outputPath = "C:\\Output\\result.txt";
File.WriteAllText(outputPath, content);
```

**AFTER (Safe)**:
```csharp
string outputPath = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments),
    "VegasOutput",
    "result.txt"
);

string directory = Path.GetDirectoryName(outputPath);
if (!Directory.Exists(directory)) {
    Directory.CreateDirectory(directory);
}

try {
    File.WriteAllText(outputPath, content);
} catch (Exception ex) {
    MessageBox.Show($"Failed to write file: {ex.Message}");
}
```

### Pattern 4: Silent Failures
**Problem**: Operations fail without user notification

**BEFORE (Unsafe)**:
```csharp
try {
    DoSomething();
} catch {
    // Silent failure - user has no idea it failed
}
```

**AFTER (Safe)**:
```csharp
try {
    DoSomething();
} catch (Exception ex) {
    MessageBox.Show(
        $"Operation failed: {ex.Message}\n\nPlease check your project and try again.",
        "Error",
        MessageBoxButtons.OK,
        MessageBoxIcon.Error
    );
    // Log for debugging
    Vegas.DebugOut($"Error in MyScript: {ex}");
}
```

### Pattern 5: Incomplete Cleanup
**Problem**: Resources not released on error

**BEFORE (Unsafe)**:
```csharp
var file = File.OpenWrite(path);
// If error occurs here, file handle leaks
WriteData(file);
file.Close();
```

**AFTER (Safe)**:
```csharp
using (var file = File.OpenWrite(path)) {
    try {
        WriteData(file);
    } catch (Exception ex) {
        MessageBox.Show($"Write failed: {ex.Message}");
        throw;
    }
} // File automatically closed even on error
```

---

## Edge Cases Checklist

When changing any script, verify behavior with:

### Timeline States
- [ ] Empty timeline (no tracks)
- [ ] Empty tracks (tracks but no events)
- [ ] Single event
- [ ] Hundreds of events
- [ ] Multiple track types (video, audio, text)
- [ ] Locked tracks
- [ ] Muted tracks

### Selection States
- [ ] Nothing selected
- [ ] Single item selected
- [ ] Multiple items selected
- [ ] Non-contiguous selection
- [ ] Entire timeline selected
- [ ] Mixed type selection (events + tracks)

### Project States
- [ ] New empty project
- [ ] Large complex project
- [ ] Project with unsaved changes
- [ ] Read-only project
- [ ] Project from older VEGAS version
- [ ] Project with missing media

### File System States
- [ ] Valid paths
- [ ] Invalid paths
- [ ] Very long paths (> 260 chars)
- [ ] Paths with spaces
- [ ] Paths with special characters
- [ ] Network paths
- [ ] Paths with unicode characters
- [ ] Read-only locations
- [ ] Full disk

### System States
- [ ] Low memory
- [ ] Slow disk I/O
- [ ] Multiple VEGAS instances
- [ ] Background processes running
- [ ] Different Windows versions
- [ ] Different system locales

---

## Performance Considerations

### Watch Out For:

**O(n²) Loops**
- Nested loops over large collections
- Repeated searches in collections
- Solution: Use dictionaries/hashtables for lookups

**Excessive UI Updates**
- Updating progress dialogs too frequently
- Refreshing UI in tight loops
- Solution: Batch updates, use background threads

**Memory Leaks**
- Not disposing IDisposable objects
- Keeping references to large objects
- Solution: Use `using` statements, clear references

**File I/O in Loops**
- Opening/closing files repeatedly
- Writing small chunks many times
- Solution: Batch operations, use buffering

---

## User Experience Anti-Patterns

### DON'T:
- ❌ Show technical stack traces to users
- ❌ Use cryptic error codes
- ❌ Freeze VEGAS during long operations
- ❌ Make irreversible changes without warning
- ❌ Assume users read documentation
- ❌ Use default exception messages

### DO:
- ✅ Show clear, actionable error messages
- ✅ Provide progress indication for long operations
- ✅ Confirm before destructive operations
- ✅ Make scripts discoverable and intuitive
- ✅ Log technical details for debugging
- ✅ Explain what went wrong in plain language

---

## Testing Strategy

### Before Committing Any Change:

1. **Smoke Test** (2 minutes)
   - Run script on simple project
   - Verify basic functionality works
   - Check for obvious errors

2. **Edge Case Test** (5 minutes)
   - Empty timeline
   - Large project
   - Invalid input
   - Verify graceful handling

3. **Integration Test** (5 minutes)
   - Test with real user workflow
   - Verify doesn't break other scripts
   - Check project file integrity

4. **Performance Check** (2 minutes)
   - Time the operation
   - Compare to baseline
   - Verify acceptable performance

**Total: ~15 minutes per change**

---

## When to Ask for Help

If you're unsure about:
- Whether a change could break existing behavior
- How to test a particular scenario
- Impact on user workflows
- Performance implications
- Backwards compatibility

**STOP and ask questions. Silent breakage is unacceptable.**

---

## Quick Decision Tree

```
Is this change necessary?
├─ NO → Don't make it
└─ YES → Could it affect existing users?
    ├─ NO → Proceed with caution
    └─ YES → Could it break silently?
        ├─ NO → Add validation, proceed
        └─ YES → STOP. Redesign approach.
```

---

## Remember

1. **Scripts are tools**: They should make life easier, not harder
2. **Users are busy**: They don't read docs or check results carefully
3. **Projects are valuable**: Never risk corrupting user work
4. **Errors happen**: Plan for them, handle them gracefully
5. **Test with reality**: Not just ideal scenarios
6. **Ask questions**: Better safe than sorry

**When in doubt, fail loudly, not silently.**
