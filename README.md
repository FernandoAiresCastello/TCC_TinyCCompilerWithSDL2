# TCC (Tiny C Compiler) + SDL 2

This is TCC (Tiny C Compiler) packaged with SDL 2.

## Notes

- The included version of TCC is **0.9.27**.
- The included version of the SDL library is **2.30.2**.
- This repository already has completed steps 1 through 6 of the setup described below. They are included here for future reference.

## Setup

1. Open CMD in a folder that contains SDL2.dll (x64)
2. Run the command "`tcc -impdef SDL2.dll`"
3. Copy the generated file "SDL2.def" to the "lib" folder of TCC
4. Copy the SDL2 headers into the "include\SDL2" folder of TCC
5. In "SDL_Config.h" change the following lines:
- FROM: `typedef unsigned int size_t`
  - TO: `typedef uint64_t size_t`
- FROM: `typedef unsigned int uintptr_t`
  - TO: `typedef uint64_t uintptr_t`
6. In "SDL_Platform.h" comment or remove the following line:
- `extern DECLSPEC const char * SDLCALL SDL_GetPlatform (void);`
7. In your "main.c" file (or whatever the source file is), use "`#include <SDL2/SDL.h>`"
8. Use "`#undef main`" immediately below the #include
9. Compile using "`tcc main.c -lSDL2`"
10. The executable is generated. Make sure the "SDL2.dll" file is in the same folder as the EXE.
