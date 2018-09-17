# neovim for linuxbrew

original neovim linuxbrew formula return '404 Not Found' ( https://luarocks.org/luabitop-1.0.2-1.src.rock )

## way1
```
brew install umaumax/neovim/neovim
```

## way2
### how to adopt patch
```
cd ~/.linuxbrew/Library/Taps/homebrew/homebrew-core
cat | patch -p1 << 'EOF'
diff --git a/Formula/neovim.rb b/Formula/neovim.rb
index 237adad..07ee17f 100644
--- a/Formula/neovim.rb
+++ b/Formula/neovim.rb
@@ -48,8 +48,8 @@ class Neovim < Formula
   end

   resource "luabitop" do
-    url "https://luarocks.org/luabitop-1.0.2-1.src.rock"
-    sha256 "fc7a8065a57462ee13bed7f95b0ab13f94ecd1bf846108c61ccf2c75548af26e"
+    url "https://luarocks.org/manifests/luarocks/luabitop-1.0.2-3.rockspec"
+    sha256 "8cc12ebd2919b08765fef9f8738d2277204e8c6a7578e8e7f1abf6054380c21f"
   end

   resource "luafilesystem" do
@@ -142,7 +142,7 @@ class Neovim < Formula
         lpeg/lpeg-1.0.1-1.src.rock
         mpack/mpack-1.0.7-0.rockspec
         inspect/inspect-3.1.1-0.src.rock
-        luabitop/luabitop-1.0.2-1.src.rock
+        luabitop/luabitop-1.0.2-3.rockspec
         luafilesystem/luafilesystem-1.7.0-2.src.rock
         lua_cliargs/lua_cliargs-3.0-1.src.rock
         lua-term/lua-term-0.7-1.rockspec
EOF
```

* maybe `<C-d>` is required?

```
brew install neovim
```
