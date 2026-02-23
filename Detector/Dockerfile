#syntax=docker/dockerfile:1
FROM ultralytics/ultralytics:latest

WORKDIR /workspace

# 시스템 패키지 + 로케일(한글 경로/출력용)
RUN apt-get update && apt-get install -y --no-install-recommends \
    git curl unzip locales \
    && sed -i 's/# ko_KR.UTF-8 UTF-8/ko_KR.UTF-8 UTF-8/' /etc/locale.gen \
    && locale-gen \
    && rm -rf /var/lib/apt/lists/ \
    && pip install --no-cache-dir ipykernel
    
# UTF-8 로케일 설정
ENV LANG=ko_KR.UTF-8 \
    LC_ALL=ko_KR.UTF-8 \
    LANGUAGE=ko_KR:ko

# ultralytics 설정/캐시 디렉토리 고정
ENV ULTRALYTICS_SETTINGS=/workspace/.ultralytics/settings.yaml \
    YOLO_CONFIG_DIR=/workspace/.ultralytics \
    MPLCONFIGDIR=/workspace/.cache/matplotlib

ENTRYPOINT ["/bin/bash"]