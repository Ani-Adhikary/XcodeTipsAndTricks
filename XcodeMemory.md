

<h2>📱 3. Delete Old Simulators </h2>

Simulators consume insane RAM + disk

Check devices:
```
xcrun simctl list

```
Delete unavailable devices:

```
xcrun simctl delete unavailable

```
Or via UI:

Xcode → Window → Devices & Simulators → delete unused ones

<h2>🗑️ 4. Clear Device Support Files - Useful </h2>

Each iOS version = GBs

```
rm -rf ~/Library/Developer/Xcode/iOS\ DeviceSupport

```

<h2>🧪 6. Clear Simulator Data (Fix RAM spikes) - Danger </h2>

```

rm -rf ~/Library/Developer/CoreSimulator/Devices

```


⚠️ This resets all simulators (clean state)

<h2>🚀 9. Pro Tip (Huge Impact) </h2>

Run this weekly:

```
rm -rf ~/Library/Developer/Xcode/DerivedData/*
rm -rf ~/Library/Developer/CoreSimulator/Caches

```
