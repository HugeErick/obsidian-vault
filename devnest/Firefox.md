## Firefox custom config (about:config)

### External and Internal Link Behavior

- Set `browser.link.open_newwindow.override.external` → `3`  
    Opens external links in a **new tab** in the **last active window** instead of a new instance.
    
- Set `browser.link.open_newwindow` → `3`  
    Ensures **internal links** also open in new tabs rather than new windows.
    

### DPI / UI Scaling

- Set `layout.css.devPixelsPerPx` → _(e.g., `1.25`)_  
    Adjusts Firefox’s **UI scaling**.  
    The default `-1.0` uses system DPI automatically.
    

### Disable Built-in Translations

- Set `browser.translations.enable` → `false`  
    Disables Firefox’s **automatic translation feature**.
    

### Never Forget Cookies

- Set `network.cookie.lifetimePolicy` → `0`  
    Ensures cookies **are kept until they expire naturally** rather than being deleted when closing the browser.