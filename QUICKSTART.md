# 🚀 Quick Start Guide - ASMR Video Workflow

## ⚡ Run the Workflow

```bash
python workflow.py
```

That's it! The workflow handles everything automatically.

## 📊 Check Progress

```bash
python show_status.py
```

Shows completion status of all ideas.

## 🔄 How It Works

### First Run
1. ✅ Creates `asmr_video_ideas.xlsx`
2. ✅ Generates 5 ASMR content ideas via Gemini
3. ✅ Creates optimized video prompt
4. ✅ Generates first video via Veo 3
5. ✅ Saves to `output/` folder
6. ✅ Updates Excel with "Completed"

### Subsequent Runs
- ✅ Checks Excel for incomplete ideas
- ✅ If found: Continues with next pending idea
- ✅ If all complete: Generates 5 new ideas
- ✅ Processes one video per run

## 📁 File Structure

```
output/                          # Generated videos
├── asmr_1_*.mp4                # Video for idea #1
├── asmr_2_*.mp4                # Video for idea #2
└── ...

logs/                            # Workflow logs
└── workflow_*.log

asmr_video_ideas.xlsx           # Tracking spreadsheet
```

## 📝 Excel Columns

| Column | Description |
|--------|-------------|
| **A** | Content idea from Gemini |
| **B** | Optimized video generation prompt |
| **C** | Status (Pending → In Progress → Completed) |
| **D** | Generated video filename |

## 🎬 Video Specs

- **Format**: MP4
- **Aspect Ratio**: 9:16 (Instagram/TikTok)
- **Quality**: 4K Cinematic
- **Duration**: ~5 seconds
- **Size**: 3-20 MB

## 💡 Tips

### Generate Multiple Videos
Run the workflow multiple times:
```bash
python workflow.py  # Generates video 1
python workflow.py  # Generates video 2
python workflow.py  # Generates video 3
```

### Generate All 5 Ideas
```bash
for i in {1..5}; do python workflow.py; done
```

### Start Fresh
Delete or rename `asmr_video_ideas.xlsx` and run again.

## ⚙️ Configuration

Edit `workflow.py` to customize:

```python
# Line 16: Change project
PROJECT_ID = "your-project"

# Line 49: Change aspect ratio
aspect_ratio="16:9"  # For YouTube
aspect_ratio="9:16"  # For Instagram/TikTok (default)
aspect_ratio="1:1"   # For Square format

# Line 98: Change idea count
ideas = generate_content_ideas(count=10)  # Generate 10 ideas
```

## 🐛 Troubleshooting

### "Failed to initialize Vertex AI"
- Check `oopsbot-8b65ad33386a.json` exists
- Verify GCP credentials are valid

### "Video generation failed"
- Check GCP quota limits
- Verify Veo 3 API is enabled
- Review `logs/workflow_*.log` for details

### Excel permission error
- Close Excel file if open
- Check file isn't read-only

## 📚 More Info

See `README.md` for complete documentation.

## 🎯 Example Output

```
✓ Generated 5 content ideas
✓ Created video prompt
✓ Video saved: output/asmr_1_Neon_paint_20251222.mp4 (3.21 MB)
✓ Excel updated

Progress: 1/5 completed (20.0%)
```

