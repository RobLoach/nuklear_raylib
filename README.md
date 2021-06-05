# raylib-nuklear

Use the [Nuklear](https://github.com/Immediate-Mode-UI/Nuklear) immediate mode cross-platform GUI library in [raylib](https://www.raylib.com/).

[![raylib-nuklear-example Screenshot](examples/raylib-nuklear-example.png)](examples)

## Example

``` c
#define RAYLIB_NUKLEAR_IMPLEMENTATION
#include "raylib-nuklear.h"

int main() {
    InitWindow(640, 480, "raylib-nuklear example");

    // Create the Nuklear Context
    struct nk_context *ctx = InitNuklear(10);

    while (!WindowShouldClose()) {
        // Update the Nuklear context, along with input
        UpdateNuklear(ctx);

        // Nuklear GUI Code
        // https://github.com/Immediate-Mode-UI/Nuklear/wiki/Window
        if (nk_begin(ctx, "Nuklear", nk_rect(100, 100, 220, 220),
                     NK_WINDOW_BORDER|NK_WINDOW_MOVABLE|NK_WINDOW_CLOSABLE)) {
            if (nk_button_label(ctx, "Button")) {
                /* event handling */
            }
        }
        nk_end(ctx);

        // Render
        BeginDrawing();
            ClearBackground(RAYWHITE);

            // Render the Nuklear GUI
            DrawNuklear(ctx);

        EndDrawing();
    }

    // De-initialize the Nuklear GUI
    UnloadNuklear(ctx);

    CloseWindow();
    return 0;
}
```

## API

``` c
struct nk_context* InitNuklear(int fontSize);  // Set a fontSize of 0 to use the default of 10.
struct nk_context* InitNuklearEx(Font font, float fontSize);
void UpdateNuklear(struct nk_context * ctx);
void DrawNuklear(struct nk_context * ctx);
void UnloadNuklear(struct nk_context * ctx);
Color ColorFromNuklear(struct nk_color color);
struct nk_color ColorToNuklear(Color color);
struct nk_colorf ColorToNuklearF(Color color);
struct Color ColorFromNuklear(struct nk_color color);
struct Color ColorFromNuklearF(struct nk_colorf color);
struct Rectangle RectangleFromNuklear(struct nk_rect rect);
struct nk_rect RectangleToNuklear(Rectangle rect);
```

## Development

### Examples
```
mkdir build
cd build
cmake ..
make
./example/raylib-nuklear-example
```

## License

*raylib-nuklear* is licensed under an unmodified zlib/libpng license, which is an OSI-certified, BSD-like license that allows static linking with closed source software. Check [LICENSE](LICENSE) for further details.
