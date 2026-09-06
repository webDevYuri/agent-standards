<!-- Project-level opt-in access controls for otherwise restricted local actions. -->

# Agent Access

Project-level opt-ins for otherwise restricted local actions:

```yaml
env_file_read: on
```

Change `off` to `on` to let an agent read project-local `.env` files when the current task requires it. Only one exact setting with literal `on` grants access; a missing, duplicate, or invalid setting remains off. Editing still requires explicit authorization in the user's current request. This never permits exposing secrets, accessing files outside the project, or contacting production or external systems.
