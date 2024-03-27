# Path Finding Unity Package
This Unity Package provides API for doing path finding with the A* search algorithm. The package also provides an interface for creating and using your own search algorithm.

## Classes

There are 3 main classes and interfaces for the path finding package.

This package includes A* implementations for the interfaces described below.

### PathFinder
This `monobehavior` serves as the API. Simply create the `Path Finder Service` prefab, or attach the `PathFinder` component to a `GameObject`.

The `PathFinder` component requires 2 objects:
 1. A search algorithm
 2. The `Path Request Event`

These components are discussed below.

#### Requesting a Path
To request a path, simply trigger the `Path Request Event` from a class the implements the `IPathRequester` interface.

Example
``` C#
public class Entity : IPathRequester
{
    PathRequestEvent requestEvent;

    OnPathFound(PathResponse)
    {
        // Implementation of IPathRequester interface
    }

    RequestPath()
    {
        requestEvent.RaiseEvent(PathRequest)
    }
} 
```

### ISearchAlgorithm
This `interface` defines the API for a search algorithm.

The `interface` requires the implemenation of a function `FindPath` that takes a `PathRequest` and a callback for the `PathResponse` the algorithm generates.

`FindPath` returns an `IEnumerator`, so that the search can be conducted in a `Coroutine`.