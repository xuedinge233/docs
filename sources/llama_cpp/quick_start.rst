快速开始
============

.. note::
    阅读本篇前，请确保已按照 :doc:`安装指南 <./install>` 准备好昇腾环境及 llama.cpp ！
    
本教程聚焦大语言模型（Large Language Model，LLM）的推理过程，以 Qwen2.5-7B 模型为例，讲述如何使用 llama.cpp 在昇腾 NPU 上进行推理。


模型文件准备及量化
---------------

llama.cpp 的推理需要使用 gguf 格式文件，llama.cpp 提供了两种方式转换 Hugging Face 模型文件：

- 使用 `GGUF-my-repo <https://huggingface.co/spaces/ggml-org/gguf-my-repo>`_ 将模型进行转换。

- 使用项目中的 `convert_hf_to_gguf.py` 文件将 Hugging Face 模型转换为 gguf 格式:

    .. code-block:: shell 
        :linenos:

        python convert_hf_to_gguf.py path/to/model

详情请参考 `Prepare and Quantize <https://github.com/ggerganov/llama.cpp/blob/master/README.md#prepare-and-quantize>`_ 。

注意：目前仅支持 FP16 精度及 Q4_0/Q8_0 量化模型。

推理
------------

有两种设备选择模式:

- 单设备：使用用户指定的一个设备目标。
- 多设备：自动选择具有相同后端的设备。

============ ==============================================
设备选择        参数                                    
============ ==============================================
单设备          --split-mode none --main-gpu DEVICE_ID 
多设备          --split-mode layer (default)           
============ ==============================================

使用单卡推理
++++++++++++++++

.. code-block:: shell 
    :linenos:

    ./build/bin/llama-cli -m path_to_model -p "Building a website can be done in 10 simple steps:" -n 400 -e -ngl 33 -sm none -mg 0

使用多卡推理
++++++++++++++++

.. code-block:: shell 
    :linenos:

    ./build/bin/llama-cli -m path_to_model -p "Building a website can be done in 10 simple steps:" -n 400 -e -ngl 33 -sm layer