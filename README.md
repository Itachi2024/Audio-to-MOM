# Audio-to-MOM: Meeting Minutes from Audio Files

Generate professional meeting minutes from audio recordings using AI-powered transcription and analysis.

## Overview

Audio-to-MOM is a Jupyter Notebook-based project that converts audio recordings of meetings into structured meeting minutes. It leverages state-of-the-art AI models for:
- **Audio Transcription**: Converting speech to text using Whisper or OpenAI's transcription service
- **Minutes Generation**: Using Llama 3.2 to analyze transcripts and produce comprehensive meeting documentation

## Features

- 🎙️ **Multiple Transcription Options**:
  - Open-source approach using Hugging Face's Whisper model
  - OpenAI's GPT-4o-mini transcription for high accuracy

- 📝 **Automated Meeting Minutes Generation** including:
  - Summary with attendees, location, and date
  - Key discussion points
  - Takeaways
  - Action items with assigned owners

- 🚀 **Google Colab Integration**: Run entirely in the cloud with GPU support
- 🔐 **Secure**: Uses Colab Secrets for API key management

## Prerequisites

### Required Accounts & APIs
- Google Colab account (for running the notebook)
- Google Drive account (for audio file storage)
- Hugging Face account (for model access)
- OpenAI API key (optional, for transcription Option 2)

### Required Tokens/Keys
- `HF_TOKEN`: Hugging Face authentication token
- `OPENAI_API_KEY`: OpenAI API key (if using Option 2 for transcription)

## Getting Started

### 1. Prepare Your Audio File

**Option A - Use the provided Denver City Council sample:**
- Download the sample audio file from [here](https://drive.google.com/file/d/1N_kpSojRR5RYzupz6nqM8hMSoEF_R7pU/view?usp=sharing)
- Upload it to Google Drive in a folder called `llms/` named `denver_extract.mp3`

**Option B - Use your own audio recording:**
- Record your meeting or prepare an existing audio file
- Upload it to Google Drive with the same path structure

**Original Dataset:**
- The project uses the [MeetingBank dataset](https://huggingface.co/datasets/huuuyeah/meetingbank) from Hugging Face

### 2. Set Up Colab Secrets

1. In Google Colab, click the "Secrets" icon (🔑) in the left sidebar
2. Add your credentials:
   - Key: `HF_TOKEN` → Value: Your Hugging Face token
   - Key: `OPENAI_API_KEY` → Value: Your OpenAI API key (if using Option 2)

### 3. Run the Notebook

1. Open [Audio_to_MOM_Meeting_Minutes.ipynb](Audio_to_MOM_Meeting_Minutes.ipynb) in Google Colab
2. Select GPU acceleration: "Runtime" → "Change runtime type" → GPU (T4)
3. Run cells sequentially from top to bottom

### 4. Workflow Overview

The notebook follows these steps:

**STEP 1: Transcribe Audio**
- Install dependencies (bitsandbytes, transformers, OpenAI client)
- Connect to Google Drive
- Choose transcription method:
  - Option 1: Whisper-medium model (open-source)
  - Option 2: OpenAI GPT-4o-mini (higher accuracy)

**STEP 2: Analyze & Report**
- Use Llama 3.2 3B Instruct model
- Generate formatted meeting minutes with:
  - Summary information
  - Discussion points
  - Key takeaways
  - Action items with owners

## Technical Stack

| Component | Tool | Details |
|-----------|------|---------|
| **Transcription** | Whisper or OpenAI | Speech-to-text conversion |
| **LLM** | Llama 3.2 3B Instruct | Meeting minutes generation |
| **Quantization** | BitsAndBytes | 4-bit quantization for efficiency |
| **Framework** | PyTorch + Transformers | Deep learning pipeline |
| **Environment** | Google Colab | Cloud-based execution with GPU |

## Troubleshooting

### CUDA Runtime Error in Colab

If you encounter: `Runtime error: CUDA is required but not available for bitsandbytes`

**Solution:**
1. Kernel menu → "Disconnect and delete runtime"
2. Edit menu → "Clear All Outputs"
3. Connect to a new T4 GPU (top-right button)
4. Verify GPU access: "View resources" from top-right menu
5. Rerun cells from the top, starting with pip installs

### Common Issues

| Issue | Solution |
|-------|----------|
| GPU not available | Verify T4 GPU is selected in Runtime settings |
| Audio file not found | Ensure file is at `/content/drive/MyDrive/llms/denver_extract.mp3` |
| HF_TOKEN not recognized | Check Colab Secrets are properly set |
| Model loading fails | Ensure sufficient GPU memory available (T4 recommended) |

## Project Structure

```
Audio-to-MOM/
├── README.md                              # This file
└── Audio_to_MOM_Meeting_Minutes.ipynb     # Main Jupyter notebook
```

## Models Used

- **Whisper-medium.en**: Open-source speech recognition model
- **meta-llama/Llama-3.2-3B-Instruct**: Lightweight LLM for text analysis
- **gpt-4o-mini-transcribe**: OpenAI's transcription model (optional)

## Use Cases

- 📋 Corporate meeting documentation
- 🏛️ Government/council meeting records
- 🎓 Academic seminar notes
- 📞 Conference call summaries
- 🤝 Team meeting documentation

## Performance Notes

- Expected runtime: 5-10 minutes (varies with audio length)
- Supports audio files of varying lengths
- GPU acceleration significantly speeds up processing

## License

This project is open source. See the repository for licensing information.

## Resources

- [MeetingBank Dataset](https://huggingface.co/datasets/huuuyeah/meetingbank)
- [OpenAI Whisper](https://openai.com/research/whisper)
- [Llama 3.2 Model](https://www.llama.com/)
- [Hugging Face Documentation](https://huggingface.co/docs)

## Contributing

Feel free to fork this repository and submit pull requests with improvements!

## Support

For issues or questions, please open an issue in the GitHub repository.

---

**Last Updated:** June 2026  
**Primary Language:** Jupyter Notebook (Python)
