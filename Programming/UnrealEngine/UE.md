# Add script to object

# Selecte VS Version
Editor Preferences - General-Source Code - Source Code Editor


# Code Analysis


FActorTickFunction::ExecuteTick()


FTickFunctionTask::DoTask()

FCollectorTaskProcessorTask::DoTask()
-> FCollectorTaskQueue::DoTask()
-> TFastReferenceCollector::ProcessObjectArray()



FFastBuildControllerModule
FFastBuildJobProcessor

```
Engine
>> Source
>> >> Runtime
>> >> >> Engine
>> >> >> >> Classes
>> >> >> >> >> GameFramework
>> >> >> >> >> >> Actor.h
>> >> >> >> >> >> ActorComponent.h
>> >> >> >> Private
>> >> >> >> >> Actor.cpp
>> >> >> >> >> ActorComponent.cpp
>> >> >> >> >> TickTaskManager.cpp
```

```
 * ActorComponent is the base class for components that define reusable behavior that can be added to different types of Actors.
 * ActorComponents that have a transform are known as SceneComponents and those that can be rendered are PrimitiveComponents.
 ```
