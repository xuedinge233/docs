安装指南
===========================

跟随指导，安装在NPU上运行的PyTorch版本。


1. 选择需要安装的 PyTorch 版本
------------------------------
准备安装 PyTorch：

.. raw:: html

    <script type="text/javascript" src="../../_static/pytorch_actions.js"></script>
    <div id="div-installation" style="">
        <div class="row">
            <div class="row-element-1" id="col-headings">
                <div class="headings-element">PyTorch版本</div>
                <div class="headings-element">PyTorch-NPU版本</div>
                <div class="headings-element">CANN-toolkit版本</div>
                <div class="headings-element">CPU架构</div>
                <div class="headings-element">安装方式</div>
            </div>
            <div class="row-element-2" id="col-values">
                <div class="row" id="row-pytorch">
                    <div class="mobile-headings">PyTorch版本</div>
                    <div class="values-element block-3 install-pytorch selected" id="pytorch-2.4.0">2.4.0</div>
                    <div class="values-element block-3 install-pytorch" id="pytorch-2.3.1">2.3.1</div>
                    <div class="values-element block-3 install-pytorch" id="pytorch-2.2.0">2.2.0</div>
                </div>
                <div class="row" id="row-pytorch_npu">
                    <div class="mobile-headings">PyTorch-NPU版本</div>
                    <div class="values-element block-1 install-pytorch_npu selected" id="pytorch_npu-version">null</div>
                </div>
                <div class="row" id="row-cann">
                    <div class="mobile-headings">CANN-toolkit版本</div>
                    <div class="values-element block-1 install-cann selected" id="cann-version">null</div>
                </div>
                <div class="row" id="row-arch">
                    <div class="mobile-headings">CPU架构</div>
                    <div class="values-element block-2 install-arch" id="arch-x86_64">x86-64</div>
                    <div class="values-element block-2 install-arch selected" id="arch-aarch64">aarch64</div>
                </div>
                 <div class="row" id="row-install_type">
                    <div class="mobile-headings">安装方式</div>
                    <div class="values-element block-3 install-type selected" id="install_type-docker">Docker</div>
                    <div class="values-element block-3 install-type" id="install_type-pip">pip</div>
                    <div class="values-element block-3 install-type" id="install_type-source">源码构建</div>
                </div>
            </div>
        </div>
    </div>


2. 安装 PyTorch
----------------

.. warning:: 

    如果使用了非CANN安装时的Python环境（如Conda），请确保CANN-toolkit依赖的Python包在该环境中已经 `安装 <../ascend/quick_install.html>`_ 。
.. raw:: html

    <section id="install-pytorch-docker-section">
        <div class="admonition note">
                <p class="admonition-title">备注</p>
                <p>请确保已经<a class="reference internal" href="../ascend/quick_install.html"><span class="doc">安装</span></a>了与上述CANN-toolkit版本匹配的驱动和固件。</p>
        </div>
        <div class="highlight">
            <pre></pre>
        </div>
    </section>
    <section id="install-pytorch-pip-section">
        <div class="admonition note">
                <p class="admonition-title">备注</p>
                <p>请确保已经根据上述表格建议<a class="reference internal" href="../ascend/quick_install.html"><span class="doc">安装</span></a>了对应的CANN-toolkit版本以及相应的固件和驱动，并应用了CANN-toolkit环境变量。</p>
        </div>
        <div class="highlight">
            <pre></pre>
        </div>
    </section>
    <div id="install-pytorch-source-section">
        <section>
            <div class="admonition note">
                <p class="admonition-title">备注</p>
                <p>请确保已经根据上述表格建议<a class="reference internal" href="../ascend/quick_install.html"><span class="doc">安装</span></a>了对应的CANN-toolkit版本以及相应的固件和驱动，并应用了CANN-toolkit环境变量。</p>
            </div>
            <h3>2.1 环境依赖</h3>
            <ul>
                <li>Python 3.8 ~ 3.10</li>
                <li>支持C++17的编译器，例如clang 或者 gcc (9.4.0及以上)</li>
                <li><a class="reference internal" href="https://docs.anaconda.com/free/miniconda/#quick-command-line-install"><span class="doc">Conda</span></a></li>
            </ul>
        </section>
        <section>
            <div class="admonition note">
                <p class="admonition-title">备注</p>
                <p>请确认CXX11_ABI是关闭的，如果无法确定，建议显式关闭：</p>
            </div>
            <div class="highlight"><pre>export _GLIBCXX_USE_CXX11_ABI=0</pre></div>
            <h3>2.2 构建</h3>
                <div class="highlight">
                    <pre></pre>
                </div>
        </section>
    </div>


3. 验证安装结果
------------------

.. code-block:: python
    :linenos:

    import torch
    import torch_npu

    x = torch.randn(2, 2).npu()
    y = torch.randn(2, 2).npu()
    z = x.mm(y)

    print(z)

程序能够成功打印矩阵Z的值即为安装成功。
