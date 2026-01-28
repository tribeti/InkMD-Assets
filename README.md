# 🎨 InkMD Assets  

![Repo Size](https://img.shields.io/github/repo-size/tribeti/InkMD-Assets?color=orange&style=flat-square)
![Last Commit](https://img.shields.io/github/last-commit/tribeti/InkMD-Assets?style=flat-square)

Welcome to the **InkMD Assets** repository. This is the centralized resource hub for the **InkMD** application. It houses all static assets and design templates required to maintain the aesthetic consistency and functionality of the InkMD app.

The repository is meticulously organized to separate UI components from content templates:

### 1. `/Icons` : 
Contains all the icons for users to display on their .md file. 

### 2. `/Templates`
A comprehensive set of predefined Markdown (`.md`) templates designed to supercharge your writing workflow.  

# If you want a new icon / template feel free to create a issue 🥰.

## Basic Usage

```
https://ink-md-server.vercel.app/api?i=html,css,js
```

## Parameters

### Required
| Parameter | Type | Description | Example |
|-----------|------|-------------|---------|
| `i` | string | Icon list (separated by commas) | `react,vue,angular` |

### Layout Options
| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `layout` | string | `h` | Layout type: `h` (horizontal), `v` (vertical), `g` (grid) |
| `columns` | number | `4` | Number of columns (only used with layout=g) |
| `size` | number | `48` | Icon size (16-256px) |
| `gap` | number | `12` | Icon gap (0-100px) |
| `padding` | number | `0` | Padding around the container |

### Styling Options
| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `theme` | string | - | Theme preset: `light`, `dark` |
| `bg` | string | transparent | Background color (hex without #) |
| `radius` | number | `0` | Border radius (px) |
| `border` | string | - | Border color (hex without #) |
| `borderWidth` | number | `0` | Border width (px) |
| `shadow` | number | `0` | Shadow intensity (0-3) |
| `glow` | boolean | `false` | Glow effect cho icons |

## 🎨 Examples

### Horizontal Layout with Dark Theme
```
https://ink-md-server.vercel.app/api?i=html,css,js&theme=dark&padding=16&radius=8&shadow=2
```

![](https://ink-md-server.vercel.app/api?i=html,css,js&theme=dark&padding=16&radius=8&shadow=2)

### Vertical Layout with Custom Background
```
https://ink-md-server.vercel.app/api?i=react,vue,angular&layout=v&bg=f0f0f0&padding=20&gap=16
```

![](https://ink-md-server.vercel.app/api?i=react,vue,angular&layout=v&bg=f0f0f0&padding=20&gap=16)

### Tech stack display
```html
<img src="https://ink-md-server.vercel.app/api?i=react,nodejs,mongodb,docker,gemini,claude,clerk,zed,winui,c,cs,dotnet,vuejs,react&layout=g&size=128&padding=16&gap=50&radius=12&glow=true" />
```
<p align="center">
<img src="https://ink-md-server.vercel.app/api?i=react,nodejs,mongodb,docker,gemini,claude,clerk,zed,winui,c,cs,dotnet,vuejs,react&layout=g&size=128&padding=16&gap=50&radius=12&glow=true" />
</p>


## 💡 Tips
1. **Theme vs. Custom BG**: Themes will be overridden if they have a `bg` parameter.
2. **Grid Layout**: Calculates the appropriate number of columns to match the number of icons to avoid empty rows.
3. **Shadow + Glow**: Can combine both to create special effects.
4. **Border**: Only visible when both `border` and `borderWidth > 0` are present.

## Color Format

All colors use hex format **without the # symbol**:
- ✅ Correct: `bg=ffffff`, `border=cccccc`
- ❌ Wrong: `bg=#ffffff`, `border=#cccccc`
