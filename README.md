# Instruction to hide the keyboard for inputs over map

### 1. First take a reference of the ComboboxInput
```
const inputRef = useRef<HTMLInputElement>(null)
<ComboboxInput
  ref={inputRef}
  className="combo-input"
  value={value}
  onChange={handleInput}
  disabled={!ready}
  // prefix={<img src='/menu-icons/map-icon.svg' />}
  placeholder={"Search location"}
  onFocus={() => {
    setSearchFocus(true)
  }}
/>
```

### 2. Take a state in the parent. We will change whenever we interact with the map
```
const [onMapInteracted, setOnMapInteracted] = useState(0)

```

### 3. Pass the state from parent to hide the keyboard using useEffect()

```
useEffect(() => {
  if (onMapInteracted) {
    inputRef?.current?.blur()
  }
}, [onMapInteracted]);

```


### 4. Chnage the value of the state on map intereaction. For example, on zoom, drag, click, etc.

```
setOnMapInteracted((onMapInteracted) => onMapInteracted + 1)
```
