# True-Anki-MCQ-Note-Template
# Advanced Multiple Choice Anki Template

A feature-rich, responsive Anki template for interactive multiple-choice cards. It supports both single & multiple correct answers, randomizes choice order, and provides detailed visual feedback to enhance your study sessions.

This template is designed to be highly configurable directly within the Anki card editor, allowing you to tailor its behavior to your personal workflow.

![MIT License](https://img.shields.io/badge/License-MIT-yellow.svg)

## Features

-   **Interactive Choices**: Click to select answers directly on the card.
-   **Multiple Correct Answers**: Supports questions where more than one choice is correct.
-   **Randomized Order**: Choices are shuffled on the front of the card to prevent memorizing their position.
-   **Detailed Feedback**: The back of the card clearly marks your answers as `Correct`, `Wrong`, or `Missed`.
-   ✨ **Dynamic Choice Disabling**: Automatically prevents you from selecting more answers than the total number of correct choices, providing a subtle hint without revealing the answer.
-   ✨ **Configurable Auto-Show**: Choose whether multiple-choice options appear immediately or are hidden behind a "Show Choices" button.
-   ✨ **Customizable Keybinds**: Edit the keyboard shortcuts used to reveal the choices.
-   🔊 **Text-to-Speech Support**: Optional TTS functionality for audio playback of questions and answers.
-   **Mobile-First Design**: Looks and works great across Anki Desktop, AnkiWeb, and AnkiMobile.

## Preview

Here is a step-by-step walkthrough of the template's features, from front to back.

<table>
  <!-- First Row of Images -->
  <tr>
    <td align="center"><strong>1. Front View</strong></td>
    <td align="center"><strong>2. Choices Shown</strong></td>
    <td align="center"><strong>3. Selecting Answers</strong></td>
  </tr>
  <tr>
    <td><img src="./assets/1-front-view.png" alt="Front of the card showing the question and Show Choices button"></td>
    <td><img src="./assets/2-choices-shown.png" alt="Multiple choice options are displayed below the question"></td>
    <td><img src="./assets/3-selecting-answers.png" alt="User actively selecting an answer from the list"></td>
  </tr>
  
  <!-- Second Row of Images -->
  <tr>
    <td align="center"><strong>4. Selection Limit Reached</strong></td>
    <td align="center"><strong>5. Correct Feedback</strong></td>
    <td align="center"><strong>6. Incorrect Feedback</strong></td>
    <td align="center"><strong>7. Easy Editing</strong></td>
  </tr>
  <tr>
    <td><img src="./assets/4-limit-reached.png" alt="Unselected choices are disabled after the maximum is selected"></td>
    <td><img src="./assets/5-back-correct.png" alt="Back of card showing a correct selection"></td>
    <td><img src="./assets/6-back-wrong.png" alt="Back of card showing an incorrect selection and the missed answer"></td>
    <td><img src="./assets/7-card-editor-view.png" alt="Anki's card editor showing the note type's fields"></td>
  </tr>
</table>

## Installation

1.  Download the latest release `.apkg` file from the [Releases page](https://github.com/anki-boi/True-Anki-MCQ-Note-Template/releases).
2.  In Anki, go to `File` > `Import...` and select the downloaded `.apkg` file.
3.  This will add the "Advanced Multiple Choice" note type to your collection. When adding new cards, select this note type.

## Card Fields

To create a card, you need to fill in the following fields:

-   **`Question`**: The question you want to ask.
-   **`Multiple Choice`**: The list of possible answers. **Separate each choice with a `<br>` tag.**
-   **`Correct Answer`**: The correct answer(s). If there are multiple, **separate each one with a `<br>` tag.** The text must exactly match the text in the `Multiple Choice` field.
-   **`Extra`**: (Optional) Any additional information, explanations, or context that will be shown on the back of the card.

## Configuration

You can easily customize the card's behavior by editing the script on the **Front Template**.

1.  Open the Anki Browser and find a card using this note type.
2.  Click the "**Cards...**" button.
3.  In the "Front Template" window, scroll to the top of the `<script>` section.

#### Automatically Show Choices

You can control whether choices are visible immediately or hidden behind a button.

```javascript
// Set to 'true' to show choices automatically.
// Set to 'false' to hide them behind a "Show Choices" button.
const AUTO_SHOW_CHOICES = true;
```

#### Customize Keybinds

If `AUTO_SHOW_CHOICES` is set to `false`, you can edit the keybinds used to trigger the "Show Choices" button.

```javascript
// Add your desired keybinds into the array below. Use lowercase letters.
// To add more keys, just add them to the list, separated by commas.
const KEY_SHOW_CHOICES = ['q', 'c'];
```

## Text-to-Speech (TTS) Support

This template supports Anki's built-in text-to-speech functionality for audio playback of card content.

### Adding TTS

To add text-to-speech to your cards, insert TTS tags in your templates:

**Front Template:**
```html
<div class="question">{{Question}}</div>
{{tts en_US:Question}}
```

**Back Template:**
```html
{{tts en_US:Question}}
{{tts en_US:Correct Answer}}
{{#Extra}}
{{tts en_US:Extra}}
{{/Extra}}
```

### TTS Configuration Options

-   **Language**: Change `en_US` to other language codes (e.g., `ja_JP` for Japanese, `es_ES` for Spanish)
-   **Voice**: Specify voices: `{{tts en_US voices=Apple_Samantha,Microsoft_Zira:Question}}`
-   **Speed**: Adjust playback speed: `{{tts en_US speed=0.8:Question}}`

### ⚠️ Important TTS Warnings

1.  **Auto-Show Choices Required**: If you enable TTS on the front template and use `AUTO_SHOW_CHOICES = false`, Anki will automatically flip the card when the audio plays. **To prevent this, you must set `AUTO_SHOW_CHOICES = true`** in the configuration.

2.  **Multiple Choice Reading Order**: TTS reads the `Multiple Choice` field content in the original order, **not** in the randomized order displayed on screen. This is because:
    -   TTS reads directly from field content before JavaScript randomization occurs
    -   There is no built-in way to make Anki's TTS read from dynamically shuffled content
    
    **Recommendation**: Only use TTS for the `Question`, `Correct Answer`, and `Extra` fields. Avoid adding TTS to the `Multiple Choice` field as it will read choices in a different order than displayed, which can be confusing.

3.  **Manual Playback**: To prevent automatic card flipping entirely, you can:
    -   Disable "Automatically play audio" in Anki settings (`Tools` → `Preferences` → `Review`)
    -   Use `autoplay=no` parameter: `{{tts en_US autoplay=no:Question}}`
    -   Press `R` during review to manually replay audio

## Recent Updates

✨ **New: Dynamic Choice Disabling**
-   When a question has multiple correct answers, the template now dynamically disables unselected choices once you have selected the maximum number of correct answers. This prevents over-selecting and serves as a subtle hint about how many answers are correct.

✨ **New: Configurable Auto-Show & Keybinds**
-   You can now easily toggle whether choices are shown automatically (`AUTO_SHOW_CHOICES = true`) or hidden behind a button (`false`).
-   If choices are hidden, you can now customize the keybinds to reveal them.

🔧 **Change: Removed Hint Button**
-   The previous "Show Hint" button and its associated text have been removed. The new dynamic choice disabling feature serves the same purpose—indicating how many choices to select—in a more intuitive and integrated way, making the old hint button redundant.

## Acknowledgements

This template utilizes a modified version of the `anki-persistence.js` script by [Simon Lammer](https://github.com/SimonLammer/anki-persistence) to preserve your selections between the front and back of the card.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
