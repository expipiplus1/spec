# SP #022: Upgrading Slang Codebase to C++20

This proposal outlines a plan to upgrade the Slang codebase from C++17 to C++20, enabling the use of modern C++ features.

## Status

Status: Design Review

Implementation: Not yet implemented

Author: Ellie Hermaszewska

Reviewer: TBD

## Background

The Slang codebase currently uses C++17. C++20 introduces several valuable features that could improve code quality, and developer quality of life. There have been requests from people contributing to the Slang codebase to make this upgrade.

## Related Work

Some large, related C++ codebases have or are migrating to C++20:

- The current Unreal Engine coding standards specify C++20
- Godot is making such a transition (some useful discussion and motivation here: https://github.com/godotengine/godot/pull/100749)

However other similar projects such as LLVM and DXC are still on C++17.

## Proposed Approach

The implementation will merely bump the language standard the slang targets are built with, and fix any breakages in a backwards compatible way. This proposal does not aim to introduce any usage of specific C++20 features, the intention is that these will organically be used as time progresses.

Documentation will need to be updated also.

## Detailed Explanation

### Compiler Requirements

Our CI already tests with C++20-compatible compilers:

- GCC 13.0
- Clang 15
- MSVC 19.26

This means we already don't test with older C++17-only compilers.

### Implementation

The implementation will focus on updating build configurations to specify C++20, with minimal code changes initially. We'll gradually adopt C++20 features where they provide clear benefits.

### Documentation Updates

We'll update documentation to reflect new compiler requirements and provide guidance for downstream users.

## Alternatives Considered

1. **Stay on C++17**:

   - Pros: No disruption to users with older compilers
   - Cons: Miss out on language improvements and modern features

2. **Skip to C++23**:

   - Pros: More features, longer before next upgrade needed
   - Cons: Limited compiler support, higher migration risk

3. **Partial adoption via feature test macros**:
   - Pros: Gradual transition, backward compatibility
   - Cons: Complex code with conditional compilation, harder maintenance
