# VLM-Large-Vision-Language-Models

Dự án này tập trung vào việc thử nghiệm mô hình Vision-Language (VLM) **Qwen2-VL-2B-Instruct** cho các bài toán hiểu ảnh, bao gồm:

- Fine-tune (LoRA) cho tác vụ mô tả/tóm tắt **hóa đơn tiếng Việt** từ ảnh.
- Chạy inference và thử nghiệm các kiểu prompting cơ bản.

## Nội dung chính

- `Qwen2VL_2B_Instruct_Tuning_ViReceipt_Sum.ipynb`: notebook fine-tune LoRA trên dataset Viet-Receipt-VQA và lưu lại model sau huấn luyện.
- `Qwen2VL_2B_Instruct_Inference.ipynb`: notebook inference/prompting (zero-shot, few-shot, CoT) trên ảnh local.

## Mô tả nhanh notebook fine-tune

`Qwen2VL_2B_Instruct_Tuning_ViReceipt_Sum.ipynb` thực hiện các bước chính:

- Load model base `unsloth/Qwen2-VL-2B-Instruct` (4-bit) và cấu hình LoRA để fine-tune.
- Load dataset `5CD-AI/Viet-Receipt-VQA` và chuyển dữ liệu về format hội thoại: user (instruction + image) -> assistant (mô tả hóa đơn).
- Huấn luyện bằng `trl.SFTTrainer` kết hợp `UnslothVisionDataCollator`.
- Chạy thử inference trong notebook và lưu model/tokenizer sau khi train.

## Yêu cầu

- Python environment có GPU (khuyến nghị) và các thư viện ML phổ biến như `torch`, `transformers`, `datasets`, `trl`, `unsloth`, `Pillow` (xem phần import trong notebook).

## Ghi chú

- Một số chuỗi tiếng Việt trong notebook có thể bị lỗi hiển thị tùy editor/encoding. Nếu gặp ký tự lạ, hãy đảm bảo bạn mở file với UTF-8.
