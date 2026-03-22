# Project Overview
This is a 2D Elevator Simulation built in the version of Unity(2022.3.21f1). It simulates a real elevator system with 3 elevators and 4 floors (Ground, 1, 2, 3). The user can press floor call buttons, and the system automatically decides which elevator should respond based on proximity, direction, and current workload. Each elevator moves smoothly, opens/closes doors, and plays sound effects at the right moments.

# Project Structure
Assets/
├── Scripts/
│   ├── ElevatorManager.cs       ← Brain of the system (dispatch logic)
│   ├── ElevatorController.cs    ← Controls each elevator individually
│   ├── ElevatorVisual.cs        ← Handles door open/close animation
│   ├── FloorButton.cs           ← Handles floor call button UI + input
│   └── SoundManager.cs          ← Manages all sound effects + volumes
├── Prefabs/
│   └── Elevator.prefab          ← Single elevator prefab (used 3 times)
├── Audio/
│   ├── buttonClick.wav          ← Plays when floor button is pressed
│   ├── doorOpen.wav             ← Plays when elevator arrives and opens
│   ├── doorClose.wav            ← Beep that plays when doors close
│   └── elevatorMoving.wav       ← Loops while elevator is travelling
└── Sprites/
    └── (shaft, floor, elevator body sprites)

# How the System Works
Player presses Floor Button
          ↓
ElevatorManager receives the request
          ↓
Scores all 3 elevators (distance + direction + idle status)
          ↓
Assigns request to the BEST scoring elevator
          ↓
That ElevatorController adds floor to its queue
          ↓
Elevator moves smoothly to target floor
          ↓
Arrives → stops → doors open → waits → doors close → next request
