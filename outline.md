### Background & Prior Works

digital IC has Verilog-Eval, hwe-bench; analog IC only has image2netlisting eval, basic 

former AI-Based Analog IC designing tools and papers focusing on specific mainstream domain. It is not universally in "Analog", but with the emergence of coding agent and virtuoso-bridge-lite, general evaluation is possible. 

[laiyao1/AnalogCoder](https://github.com/laiyao1/AnalogCoder)

Razavi SSC-M / ISSCC Forum 2026 analog homework evaluation.

David Pan.

Why no layout? Text-Based LLM cannot. Similar to Go Game

### Benchmark Types

PPA, design time (input tokening time, output tokeging time, thinking time, simulation time, Virtuoso Bridge Tool calling time), cost?, with and wthout 

only Pass@1

How many times to try one test to get a valid result?

simulation time is crital for AI Agent, for AI are not as smart (have "insight") as human, but can tirelessly tring simulation. Cadence Spectre X is too slow to start and finish for a very simple and basic sub-blocks in the iteration, 50s to start and get a results. ALPS from empyrean is adopted to speed up simulation time. Pie chart to breakup time?

#### Clear Target Evaluation


|                            | Analog                                            | Mixed-Signal                                   | RF   | Custom-Digital          | Target | Human Expert Time (pre-sim only) | Human Expert Simulation Run |
| -------------------------- | ------------------------------------------------- | ---------------------------------------------- | ---- | ----------------------- | ------ | -------------------------------- | --------------------------- |
| Level 0                    | Common Source                                     |                                                |      | Inverters               |        | < 5 min                          | 1                           |
| Level 1                    | 5T-OTA                                            |                                                |      | AOI Gate                |        | < 0.5h                           | 1~3                         |
| Level 2                    | Two-Stage Miller compensated Amp                  | StrongArm Comparator / Bootstrap               |      | TSPC Logic / DFF / SRAM |        | < 5h                             | 10                          |
| Level 3                    | Fully Diffential Folded Cascode Gain Boosting Amp | VCM-based Asyn 8-bit 500MHz SAR ADC            |      |                         |        | < 2 days                         | 50                          |
| Level 4                    | Three stage Amp?                                  | 4-bit Flash ADC with time-domain interpolation |      |                         |        | < 7 days                         | 200                         |
| Level 5 Paper Reproduction | 2000 - 2026 simple paper                          |                                                |      |                         |        | < 30 days                        | 1000                        |
| Level 6 Chip Reproduction  | 2000 - 2026 simple paper + PVT                                       |                                                |      |                         |        |                                  |                             |


- Level 0
  - showing the very basic analog IC knowledge and tool calling
- Level 1
  - 
- Level 5
  - Can be used as an tool to aid post-evaluate academic fraud, if in 2040 the AI is realy strong and still cannot reproduce a paper in the year of 2026 after "wisely" exploring all the design space?

#### Blur Target Evaluation (Need the AI Agent to Choose Architect First)

|         |                                                |      |      |      |      |
| ------- | ---------------------------------------------- | ---- | ---- | ---- | ---- |
| Level 0 |                                                |      |      |      |      |
| Level 1 | Bandgap / 50GS/s 8-bit bootstrap               |      |      |      |      |
| Level 2 | Basic ADC: 5G 7-bit Power as Lower as possible |      |      |      |      |
|         |                                                |      |      |      |      |


- 全国大学生集成电路创新创业大赛
- 中国研究生创芯大赛
- 全國大專院校IC設計競賽

### Scaffolding / Harness

- Codex / Claude Code / Gemini CLI / Kimi CLI / Qwen Code -> Virtuoso Bridge Lite -> Virtuoso

use local version of virtuoso-bridge instead of ssh one to minimize the tool overheads

### Detailed Dataset

#### Clear Target Evaluation

##### Level 0

##### Level 1

##### Level 2

```markdown
Skim the code repository briefly, then proceed to design a two-stage amplifier with Miller compensation. The first stage is a PMOS-input 5T-OTA, and the second stage is an NMOS-input common‑source. Use Miller compensation (Miller capacitor Cc + zero‑setting resistor Rz) between the two stages. The PMOS tail current transistor of the first stage and the PMOS load of the second stage share a diode‑connected PMOS current‑mirror transistor for biasing. Thus, there are a total of 1 + 5 + 2 transistors.

Supply voltage = 1 V
Open‑loop gain > 60 dB
Unity‑gain bandwidth > 150 MHz
Phase margin > 60°
Load capacitance CL = 10 pF
Power consumption: <1.5 mA

List the estimation formulas for the dominant pole, the second pole, the zero, and the unity‑gain bandwidth (appropriate approximations may be used). You may run small experiments to explore, and you should also perform theoretical analysis of the transfer function, etc., thinking while simulating—don’t just do a pure “spice monkey” approach.  
Design the value of the compensation capacitor Cc, using a zero‑adjusting resistor.  
Design the bias currents. Under the requirement constraints, keep the total current as low as possible.
Provide the sizing for all transistors.
Present simulated Bode plots (frequency range 1 Hz to 10 GHz).

There are no other restrictions, so you don’t need to ask me anything—just start exploring and iterating on your own. Do not stop iterating until the specifications are met. If you need any interface assistance, let me know.
```

##### Level 3
