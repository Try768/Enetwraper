import os
import sys

from methods import print_error

# ===== Validasi OS =====
if os.name != "nt":
    print_error("This SConstruct is Windows-only (x64).")
    Exit(1)

# ===== Environment =====
env = Environment(
    tools=["default", "msvc"],
    PLATFORM="windows",
    TARGET_ARCH="x86_64",
)

# ===== Build flags =====
env.Append(
    CPPDEFINES=["WIN32", "_WINDOWS"],
    CPPPATH=[
        "src/",
        "include/",
    ],
    LIBPATH=[
        "lib/",
    ],
    LIBS=[
        "user32",
        "ws2_32",
    ],
)

# ===== Source =====
sources = Glob("src/*.cpp")

# ===== Output =====
target = env.SharedLibrary(
    target="bin/windows/myextension",
    source=sources,
)

Default(target)
