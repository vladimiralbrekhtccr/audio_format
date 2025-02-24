# Audio Dataset Format Specification

## Dataset Structure
The dataset can contain two types of entries: single audio and multiple audio formats.

### 1. Single Audio Format
```json
{
  "id": 0,
  "audio": "audios/1.wav",
  "audio_length_seconds": 1.0,
  "conversations": [
    {
      "from": "human",
      "value": "<audio>\nSummarize this audio"
    },
    {
      "from": "gpt",
      "value": "In this audio the command 'forward' was given"
    }
  ]
}
```

### 2. Multiple Audio Format
```json
{
  "id": 0,
  "audios": ["audios/0_0.wav", "audios/0_1.wav"],
  "audio_length_seconds": [4.09, 9.72],
  "conversations": [
    {
      "from": "human",
      "value": "<audio>\nОсы дыбыс жазбаларындағы мәтінді анықтай аласыз ба? Сөйлеушілер мен уақыт туралы ақпаратты қосыңыз."
    },
    {
      "from": "gpt",
      "value": "In audio 1 (female speaker 3, 0.00s - 4.09s): \"Биыл қала тұрғындары мен қонақтары жаңа лептегі мерекеге куә болмақ.\"\nIn audio 2 (female speaker 4, 4.09s - 13.81s): \"Сондай-ақ Алматыда ашылған Біріккен Ұлттар Ұйымының ғимаратына Орталық Азия мәселесін шешуге арналған тұрақты даму мақсаттары жөніндегі орталықты ашу қажеттігін айтты.\""
    }
  ]
}
```

## Length Requirements
* Single audio files must not exceed 30 seconds in length
* For multiple audio entries, the combined length must not exceed 150 seconds
* The format structure must strictly follow the examples provided above

## Required Fields
* `id`: Unique identifier for the entry
* `audio`/`audios`: Path to audio file(s)
* `audio_length_seconds`: Duration of audio file(s)
* `conversations`: Array of human-AI interactions with `from` and `value` fields
