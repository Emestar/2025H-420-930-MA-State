# State Pattern Refactoring Exercise

## Objective
Refactor the existing `TrafficLight` class to use the **State Pattern** instead of the current if-elif-else implementation.

## Current Implementation Problems

The current `TrafficLight` class in `src/state/state.py` has several issues:

1. **Repetitive if-elif-else statements** - Similar conditional logic appears in multiple methods
2. **Difficult to extend** - Adding new states requires modifying multiple methods
3. **Scattered state behavior** - State-specific logic is spread throughout the class
4. **Hard to test** - Cannot easily test individual state behaviors in isolation
5. **Violates Open/Closed Principle** - Class is not open for extension, closed for modification

## Your Task

Refactor the code to implement the **State Pattern** with the following structure:

### 1. Create Abstract State Class
```python
from abc import ABC, abstractmethod

class TrafficLightState(ABC):
    @abstractmethod
    def handle_tick(self, context):
        pass
    
    @abstractmethod
    def get_instruction(self):
        pass
    
    @abstractmethod
    def can_pedestrians_cross(self):
        pass
    
    @abstractmethod
    def handle_emergency(self, context):
        pass
    
    @abstractmethod
    def handle_pedestrian_request(self, context):
        pass
    
    @abstractmethod
    def get_display_name(self):
        pass
```

### 2. Create Concrete State Classes
- `RedLightState`
- `YellowLightState` 
- `GreenLightState`
- `MaintenanceState`

### 3. Modify TrafficLight Class
- Replace state string with state object
- Delegate state-specific behavior to current state object
- Implement state transition logic

## Requirements

✅ **Must implement all existing functionality**
- Normal traffic light cycling (Red → Green → Yellow → Red)
- Emergency override capability
- Pedestrian crossing requests
- Maintenance mode
- All timing and display features

✅ **Must follow State Pattern principles**
- Each state is its own class
- State-specific behavior is encapsulated in state classes
- Context (TrafficLight) delegates to current state
- Easy to add new states without modifying existing code

✅ **Must maintain the same public interface**
- All existing public methods should work the same way
- The `main()` function should run without changes

## Bonus Challenges

🌟 **Add new states** (after completing basic refactoring):
- `FlashingRedState` - For school zones
- `ArrowGreenState` - For turn signals
- `NightModeState` - Flashing yellow at night

🌟 **Add state transition validation**
- Ensure only valid state transitions are allowed
- Log state changes

🌟 **Add configuration**
- Make timing durations configurable per state
- Allow different timing profiles (normal, rush hour, night)

## Testing Your Solution

Run the existing main function to verify your refactoring works:

```bash
uv run main
```

The output should be identical to the original implementation.

**Run the test suite to verify all functionality:**

```bash
uv run python test_traffic_light.py
```

All tests should pass if your State Pattern implementation is correct.

## Hints

1. Start by creating the abstract state class
2. Implement one concrete state at a time
3. Test each state individually before integrating
4. Use the Context pattern - pass the TrafficLight instance to state methods when needed
5. Consider using properties for timing configurations
6. Remember: each state knows what the next state should be

## Success Criteria

- [ ] All if-elif-else statements related to state are eliminated
- [ ] Each state is its own class with encapsulated behavior
- [ ] Adding a new state requires no changes to existing state classes
- [ ] The TrafficLight class is simplified and only manages state transitions
- [ ] All original functionality is preserved
- [ ] Code is more maintainable and testable

Good luck! 🚦
