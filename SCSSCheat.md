# SCSS Cheat Sheet

## Variables

```scss
$primary: #3498db;
$padding: 10px;

.button {
  color: $primary;
  padding: $padding;
}
```

---

## Nesting

```scss
.nav {
  ul {
    list-style: none;
  }

  li {
    color: red;
  }
}
```

---

## Parent Selector (&)

```scss
.button {
  background: blue;

  &:hover {
    background: red;
  }
}
```

---

## Mixins (Reusable styles)

```scss
@mixin flexCenter {
  display: flex;
  justify-content: center;
  align-items: center;
}

.box {
  @include flexCenter;
}
```

---

## Functions

```scss
@function double($value) {
  @return $value * 2;
}

.box {
  width: double(10px);
}
```

---

## Partials & Import

```scss
// _variables.scss
$color: red;

// main.scss
@use 'variables';

.box {
  color: variables.$color;
}
```

---

## Extend (Reuse styles)

```scss
%center {
  display: flex;
  justify-content: center;
}

.box {
  @extend %center;
}
```

---

## Operators

```scss
.box {
  width: 100px + 50px; // 150px
}
```

---

## Condition (if/else)

```scss
$theme: dark;

body {
  background: if($theme == dark, black, white);
}
```

---

## Loop

```scss
@for $i from 1 through 3 {
  .m-#{$i} {
    margin: #{$i * 10}px;
  }
}
```

---

## Quick Tips

* Use variables for colors & spacing
* Use mixins for reusable logic
* Prefer @use over @import
* Keep nesting max 2–3 levels
* Use partials for large projects

---

If you want, Pandey Ji, next I can give:
👉 **SCSS structure for large React/Next apps (folder-wise best practice)**
