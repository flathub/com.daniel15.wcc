This is the Flathub repository for [WebCamControl](https://github.com/Daniel15/WebCamControl).

# Building
```
# Download dependencies
flatpak install -y flathub org.flatpak.Builder
flatpak-builder build-dir --user --install-deps-from=flathub --download-only com.daniel15.wcc.yaml

# Update NuGet dependencies
wget https://raw.githubusercontent.com/flatpak/flatpak-builder-tools/master/dotnet/flatpak-dotnet-generator.py
python3 flatpak-dotnet-generator.py --dotnet 8 --freedesktop 24.08 nuget-sources.json ../WebCamControl/src/WebCamControl.Gtk/WebCamControl.Gtk.csproj

# Lint
flatpak run --command=flatpak-builder-lint org.flatpak.Builder manifest com.daniel15.wcc.yaml

# Build
flatpak-builder build-dir --user --install-deps-from=flathub com.daniel15.wcc.yaml --force-clean --install

# Test
flatpak run com.daniel15.wcc
```
