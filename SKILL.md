---
name: kaipai-web-precise-edit
description: Create a Kaipai Web "网感剪辑" video with selected caption styling and transcript-based pause removal. Use when a user supplies local video and explicitly wants the Kaipai web editor, not the Kaipai CLI or API.
---

# Kaipai Web Precise Edit

Use **Ego Browser** for every website navigation, upload, setting change, task submission, and download in this workflow. It is for single-speaker Chinese talking-head footage; for other material, stop after analysis and ask the user whether to force this treatment or choose another workflow.

## Upload and analysis

- Open `https://www.kaipai.com/ai-edit` and upload the user-provided local video through its file input only after the user has authorized uploading that specific file to Kaipai.
- Keep one upload session. The page can show 100% while it performs server-side language detection and intelligent sentence splitting; wait in the existing session and do not upload the same file again. Do not end the browser task while Kaipai is processing: check progress every 60 seconds and automatically move to the next step once the current stage completes.
- Open the new task's **编辑** control once analysis has completed and wait for the editor's actual duration and timeline to load.

## Precise pause editing

Do this before choosing a visual template or processing the video.

- Open **文字快剪** and inspect every portion of the virtualized transcript list by scrolling the list from beginning to end.
- Remove the user-requested silent / hesitation segments with the menu action **删除字幕及画面**. Re-scan after each deletion: adjacent pauses can merge or all following timestamps can shift.
- Remove every detected `无声片段`, regardless of duration. Apply a threshold only when the user explicitly gives one.
- At the opening, remove generic ordinal label fragments such as `第 X 条` so the video starts directly with the substantive statement.
- Normalize the product name as `GPT` in the editable transcript/captions before processing. Replace lowercase or mixed-case standalone uses (for example, `gpt`, `Gpt`, `gptplus`) without altering unrelated words.
- Never delete spoken content merely because it is short. Keep complete, intelligible spoken units and delete only silence, clear false starts, or retakes the user has asked to remove.

## Styling and sound

- Select the template requested by the user by clicking the template card itself, not just its name. Confirm it receives the active state before processing.
- Use **基础白金** unless the user requests another template.
- Enable both **音乐** and **音效** by default and verify both checkboxes are checked. Let Kaipai automatically match the music unless the user supplies mood direction.
- If the user explicitly wants original audio unchanged, override that default by turning both additions off and verifying both checkboxes are unchecked. Do not otherwise change the **声音** settings.

## Process, export, and verify

- Clicking **开始处理** can consume Kaipai entitlements. For a single video, proceed once the user has explicitly asked to generate it; for a batch, obtain one summary confirmation before the first submission.
- Wait through the server-side packaging states rather than returning early. If a stage has no progress for 10 minutes, do not re-upload, cancel, or retry; keep the task open, report the condition, and continue waiting unless the user changes direction.
- Click **导出**, keep the requested or default 1080P MP4 option, then click **导出视频**.
- Wait for the final render dialog to say **生成完成** before selecting **下载视频**. Save the received browser download to the Desktop as `原文件名-网感精剪-YYYYMMDD-HHMM.mp4`, without overwriting an existing file, and verify that it exists before reporting local delivery.
- If Kaipai marks a task 已导出 but no browser download event or local file appears, report the web export as complete but do not claim a local file was delivered.
