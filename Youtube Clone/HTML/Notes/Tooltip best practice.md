### **Best Practice for Creating a Tooltip: `opacity` vs. `display`**
Using `opacity` is **better** than `display` for tooltips because it allows **smooth transitions** and **doesn't remove the element from the layout**.

---

### **✅ Best Practice: Use `opacity` + `visibility`**
```css
.tooltip {
  position: relative;
  display: inline-block;
}

.tooltip .tooltip-text {
  position: absolute;
  background-color: black;
  color: white;
  padding: 5px 10px;
  border-radius: 5px;
  font-size: 14px;
  white-space: nowrap;
  
  bottom: 120%;
  left: 50%;
  transform: translateX(-50%);
  
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.3s ease-in-out, visibility 0.3s;
}

.tooltip:hover .tooltip-text {
  opacity: 1;
  visibility: visible;
}
```
```html
<div class="tooltip">
  Hover me
  <span class="tooltip-text">Tooltip message</span>
</div>
```

### **💡 Why Use `opacity` + `visibility`?**
✔ **Smooth fade-in/out effect** (instead of sudden appearance/disappearance).  
✔ **Doesn’t remove the tooltip from layout** (avoids page reflow).  
✔ `visibility: hidden;` prevents it from being interactive when hidden.  

---

### **🚫 Why Not `display: none`?**
- **`display: none;` completely removes the tooltip from the DOM**, causing a **layout shift** when it appears.
- No smooth transitions because **you can’t animate `display`**.

---

### **🔥 Alternative: Use `scale` for Pop-Up Effect**
```css
.tooltip-text {
  transform: scale(0);
  transition: transform 0.3s ease-in-out;
}

.tooltip:hover .tooltip-text {
  transform: scale(1);
}
```
**Good for:** Tooltips that "pop in" instead of fade.

---

### **🚀 Final Answer**
**Best practice:** ✅ Use `opacity: 0` + `visibility: hidden`, with `transition`.  
**Avoid:** ❌ `display: none;` because it removes the tooltip completely and can't be animated.  

Let me know if you need more refinements! 🎯🔥