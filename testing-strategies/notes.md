# CCNA Study & Testing Strategy

## Core Study Flow

1. **Transfer notecards to Google Docs**
   - Consolidate scattered notes into a single reference document (Jeremy's Anki Flashcards)

2. **Watch all Professor Messer Net+ videos**
   - Solidify foundational knowledge

3. **Run the entire Google Doc through ChatGPT**
   - **For commands**: Create hypothetical real-world scenarios where each command would be used  
   - **For everything else**:
     - Break down nuances of every standard  
     - Physically write out tables and facts  
     - Learn each protocol from an engineering and best practice standpoint

4. **Watch all Jeremy’s IT Lab videos**
   - Use for context and as a refresher

5. **Test with Boson**
   - Use the Boson discount code
   - For every answer (right or wrong), analyze it with ChatGPT:
     - Why was it wrong?
     - Why was the right answer correct?

---

## Core Routing Protocol Basics

Routing protocol operations generally follow these steps:

- Exchange of information on interfaces to discover neighboring routers
- Exchange of routes that have been advertised
- Running of the algorithm to determine the best path
- Adding of best paths to the routing table
- Detection of topology changes and updating accordingly

> These are general steps. Each routing protocol differs and will be covered later.

---

## Chat Expansion Prompt Template

### Refined CCNA Prompt Template

---

### Default Behavior Check

- What is the default state (enabled/disabled)?
- What does it look like in the CLI (`show run`, `show xyz`)?
- How would you verify it in a live router/switch?

---

### Real-World Application

- Where does this show up in actual networks?
- What misconfigurations or issues does it commonly cause?
- What’s the impact if it's ignored?

---

### Exam + Boson Angle

- How would Boson quiz this? (trick wording, subtle command differences)
- How would Cisco phrase it on the CCNA? (lab sim, multi-choice, drag/drop)
- What answers would be easy to fall for? (gotcha traps)

---

### Concept Expansion

- Related topics (e.g., if it’s DHCP Snooping → tie in ARP Inspection, VLAN trust)
- Pitfalls and corner cases
- Lab verification steps

---

### Command Table

- CLI commands + purpose
- Include relevant `show`, `config`, and `debug` commands
- Mention command output cues (what to look for)

---

### Related Technologies or Dependencies

- What else must be enabled/disabled for this feature to work?
- What breaks if this config is missing?

---

### Error Messages / Logs

- What syslog/debug messages appear if this feature fails?
- What output from `show log` or `debug` gives it away?

---

### Cheat Mnemonic or Memory Hook

- A simple way to memorize key behavior or command pairing  
  _Example: “LLDP = Listen/Leak, PAgP = Proprietary Auto Game Plan”_

---

### Mini Scenario

- 1–2 sentence real-world use case or Boson-like mini-question
- Helps cement the idea through micro-context
