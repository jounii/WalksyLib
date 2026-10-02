# Minecraft 26.3 Fabric port

Use JDK 25, Fabric Loader 0.19.5 and Fabric API 0.161.0+26.3.
Mod Menu 21.0.0 exposes the configuration screens.

```sh
./gradlew build publishMavenJavaPublicationToWorkspaceRepository
```

The workspace publication writes `main.lib:WalksyLib:1.0.13+26.3` into
`../.maven-local` for sibling fork builds. This is a local development release;
no artifact has been published to Modrinth or a remote Maven repository.

The port migrates RenderPipeline to RenderPearl, GLFW input and file drops to
the SDL-compatible vanilla APIs, shield disabling to weapon components, and
the blur uniform injection to the new descriptor. The settings screen creates
the current frame's graphics context before registered widgets render, fixing
a first-frame SearchBarWidget crash and stale graphics context use.

Validation: build and local publication passed. A development client loaded
this library with all three dependent ports, and their Mod Menu configuration
screens each rendered for 30 client ticks without crashing. The user confirmed
the repaired screen works in their instance. Broader configuration interaction
and multiplayer testing remain incomplete. Settings translucency follows the
original background implementation.
