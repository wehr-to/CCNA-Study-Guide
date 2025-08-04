# Data Serialization Formats

## YAML

- YAML files start with `---` (three hyphens)
- YAML key-value pairs are represented as `key: value`
- In YAML, `-` indicates a list
- In YAML, **whitespace is significant**

**Q: What does YAML stand for?**  
YAML Ain't Markup Language

## XML

- XML uses the `<key>value</key>` format
- In XML, **whitespace isn’t significant**

**Q: What does XML stand for?**  
Extensible Markup Language

## JSON

- In JSON, **whitespace isn’t significant**
- A JSON boolean can be `true` or `false`
- A JSON Null data type represents the intentional absence of any value
- A JSON Object is a list of key-value pairs
- A JSON Number is a numeric value
- A JSON Array is a series of values
- A JSON String is a text value

### Common JSON Types
```json
"Key": "value"                                  // String  
"Key": 5                                        // Number  
"key": ["yes", "no"]                            // Array  
"Key": false                                    // Boolean  
"Key": null                                     // null  
"key": {"interface": "gigabitethernet1/1"}      // Object  
```

### JSON Data Type Categories

**Primitive Types:**
- String  
- Number  
- Boolean  
- Null  

**Structured Types:**
- Object  
- Array  

**Q: What does JSON stand for?**  
JavaScript Object Notation

## General

**Q: Which data serialization languages are often used by REST APIs?**  
- JSON  
- XML  
