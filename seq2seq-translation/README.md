# Alien Language Translator

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![PyTorch](https://img.shields.io/badge/PyTorch-1.9+-red.svg)](https://pytorch.org/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

## 🌟 Описание проекта

Этот проект представляет собой систему машинного перевода с инопланетного языка на английский. Модель обучена на специально сгенерированных данных, имитирующих коммуникацию с инопланетной цивилизацией.

Проект создан в рамках учебных материалов от **Яндекс тренировок по ML 2.0** и демонстрирует применение современных методов глубокого обучения для задачи sequence-to-sequence перевода.

## 🎯 Задача

Разработать нейросетевую модель, способную переводить тексты с неизвестного (инопланетного) языка на английский язык. Входные данные представлены в виде геометрических символов и специальных знаков, которые нужно интерпретировать и перевести на человеческий язык.

## 🧠 Архитектура модели

### Seq2Seq с механизмом внимания

Модель реализует классическую архитектуру Sequence-to-Sequence с механизмом внимания:

- **Encoder**: Двунаправленная GRU с embedding слоем
- **Attention Mechanism**: Luong-style attention для фокусировки на релевантных частях входной последовательности
- **Decoder**: GRU декодер с механизмом внимания для генерации перевода
- **Tokenization**: BPE (Byte Pair Encoding) для обеих языковых модальностей

### Основные компоненты:

1. **Encoder** (`Encoder` class)
   - Bidirectional GRU для захвата контекста в обоих направлениях
   - Embedding слой для преобразования токенов в векторные представления

2. **Attention** (`Attention` class)
   - Механизм внимания для вычисления весов важности различных частей входной последовательности

3. **Decoder** (`Decoder` class)
   - GRU с механизмом внимания для последовательной генерации перевода

4. **Seq2Seq** (`Seq2Seq` class)
   - Объединяющая модель, реализующая полный pipeline перевода

## 📊 Данные

https://disk.yandex.ru/d/u8mmcUBn64p_Nw

Датасет содержит:
- **Тренировочные данные**: 300,000 пар "инопланетный текст - английский перевод"
- **Валидационные данные**: 500 пар для оценки качества
- **Тестовые данные**: 1,000 примеров для финальной оценки

Формат данных:
```json
{"src": "► ◝▴▦ ◀◣◳▱◪ ◀◗◓◫ ◈◪◐◫▱◗◎", "dst": "Hello world this is alien message"}
