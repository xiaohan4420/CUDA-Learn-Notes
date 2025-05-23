# Swish

## 0x00 说明

包含以下内容：

- [X] swish_f32_kernel
- [X] swish_f32x4_kernel(float4向量化版本)
- [X] swish_f16_kernel(fp16版本)
- [X] swish_f16x2_kernel(fp16向量化版本)
- [X] swish_f16x8_kernel(fp16向量化版本)
- [X] swish_f16x8_pack_kernel(fp16向量化，pack版本)
- [X] PyTorch bindings


## 测试

```bash
# 只测试Ada架构 不指定默认编译所有架构 耗时较长: Volta, Ampere, Ada, Hopper, ...
export TORCH_CUDA_ARCH_LIST=Ada
python3 swish.py
```

输出:

```bash
-------------------------------------------------------------------------------------
                                        S=1024, K=1024
           out_f32: ['0.46177661  ', '-0.10888041 '], time:0.01246500ms
         out_f32x4: ['0.46177661  ', '-0.10888041 '], time:0.01006508ms
        out_f32_th: ['0.46177667  ', '-0.10888041 '], time:0.03012419ms
-------------------------------------------------------------------------------------
           out_f16: ['0.46191406  ', '-0.10894775 '], time:0.01299334ms
         out_f16x2: ['0.46191406  ', '-0.10894775 '], time:0.01036119ms
         out_f16x8: ['0.46191406  ', '-0.10894775 '], time:0.00979590ms
     out_f16x8pack: ['0.46191406  ', '-0.10894775 '], time:0.00972557ms
        out_f16_th: ['0.46191406  ', '-0.10888672 '], time:0.02423882ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=1024, K=2048
           out_f32: ['-0.27797085 ', '0.71514565  '], time:0.01415992ms
         out_f32x4: ['-0.27797085 ', '0.71514565  '], time:0.01159716ms
        out_f32_th: ['-0.27797085 ', '0.71514559  '], time:0.02964258ms
-------------------------------------------------------------------------------------
           out_f16: ['-0.27807617 ', '0.71582031  '], time:0.01473880ms
         out_f16x2: ['-0.27807617 ', '0.71582031  '], time:0.01404881ms
         out_f16x8: ['-0.27807617 ', '0.71582031  '], time:0.01127148ms
     out_f16x8pack: ['-0.27807617 ', '0.71582031  '], time:0.01101518ms
        out_f16_th: ['-0.27807617 ', '0.71533203  '], time:0.02657008ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=1024, K=4096
           out_f32: ['0.29988611  ', '-0.2541697  '], time:0.01959276ms
         out_f32x4: ['0.29988611  ', '-0.2541697  '], time:0.01605868ms
        out_f32_th: ['0.29988611  ', '-0.25416973 '], time:0.03745818ms
-------------------------------------------------------------------------------------
           out_f16: ['0.30004883  ', '-0.25415039 '], time:0.02078271ms
         out_f16x2: ['0.30004883  ', '-0.25415039 '], time:0.01729155ms
         out_f16x8: ['0.30004883  ', '-0.25415039 '], time:0.01489425ms
     out_f16x8pack: ['0.30004883  ', '-0.25415039 '], time:0.01351643ms
        out_f16_th: ['0.29980469  ', '-0.25415039 '], time:0.03149080ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=2048, K=1024
           out_f32: ['-0.07777861 ', '-0.27842814 '], time:0.01640201ms
         out_f32x4: ['-0.07777861 ', '-0.27842814 '], time:0.01180029ms
        out_f32_th: ['-0.07777861 ', '-0.27842814 '], time:0.02952218ms
-------------------------------------------------------------------------------------
           out_f16: ['-0.07775879 ', '-0.27856445 '], time:0.01758027ms
         out_f16x2: ['-0.07775879 ', '-0.27856445 '], time:0.01236153ms
         out_f16x8: ['-0.07775879 ', '-0.27856445 '], time:0.01109338ms
     out_f16x8pack: ['-0.07775879 ', '-0.27856445 '], time:0.01091790ms
        out_f16_th: ['-0.07775879 ', '-0.27856445 '], time:0.02657914ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=2048, K=2048
           out_f32: ['-0.14754841 ', '-0.21989606 '], time:0.01957679ms
         out_f32x4: ['-0.14754841 ', '-0.21989606 '], time:0.01496792ms
        out_f32_th: ['-0.14754841 ', '-0.21989603 '], time:0.03751612ms
-------------------------------------------------------------------------------------
           out_f16: ['-0.14758301 ', '-0.21984863 '], time:0.02085924ms
         out_f16x2: ['-0.14758301 ', '-0.21984863 '], time:0.01961517ms
         out_f16x8: ['-0.14758301 ', '-0.21984863 '], time:0.01386237ms
     out_f16x8pack: ['-0.14758301 ', '-0.21984863 '], time:0.01334929ms
        out_f16_th: ['-0.14758301 ', '-0.21984863 '], time:0.03151488ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=2048, K=4096
           out_f32: ['1.07876182  ', '-0.27844051 '], time:0.03036070ms
         out_f32x4: ['1.07876182  ', '-0.27844051 '], time:0.02339220ms
        out_f32_th: ['1.07876182  ', '-0.27844048 '], time:0.05310464ms
-------------------------------------------------------------------------------------
           out_f16: ['1.078125    ', '-0.27832031 '], time:0.03291988ms
         out_f16x2: ['1.078125    ', '-0.27832031 '], time:0.02590466ms
         out_f16x8: ['1.078125    ', '-0.27832031 '], time:0.02027988ms
     out_f16x8pack: ['1.078125    ', '-0.27832031 '], time:0.01811814ms
        out_f16_th: ['1.07910156  ', '-0.27832031 '], time:0.04083204ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=4096, K=1024
           out_f32: ['0.31169948  ', '-0.18232882 '], time:0.02427077ms
         out_f32x4: ['0.31169948  ', '-0.18232882 '], time:0.01515222ms
        out_f32_th: ['0.31169948  ', '-0.18232881 '], time:0.03754425ms
-------------------------------------------------------------------------------------
           out_f16: ['0.31152344  ', '-0.18237305 '], time:0.02679300ms
         out_f16x2: ['0.31152344  ', '-0.18237305 '], time:0.01617312ms
         out_f16x8: ['0.31152344  ', '-0.18237305 '], time:0.01357770ms
     out_f16x8pack: ['0.31152344  ', '-0.18237305 '], time:0.01324248ms
        out_f16_th: ['0.31152344  ', '-0.18225098 '], time:0.03149295ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=4096, K=2048
           out_f32: ['1.5033319   ', '0.17473438  '], time:0.03030729ms
         out_f32x4: ['1.5033319   ', '0.17473438  '], time:0.02150083ms
        out_f32_th: ['1.5033319   ', '0.17473438  '], time:0.05257607ms
-------------------------------------------------------------------------------------
           out_f16: ['1.50390625  ', '0.17468262  '], time:0.03289509ms
         out_f16x2: ['1.50390625  ', '0.17468262  '], time:0.03073120ms
         out_f16x8: ['1.50390625  ', '0.17468262  '], time:0.01862860ms
     out_f16x8pack: ['1.50390625  ', '0.17468262  '], time:0.01772857ms
        out_f16_th: ['1.50390625  ', '0.17468262  '], time:0.04082441ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=4096, K=4096
           out_f32: ['-0.05288643 ', '-0.14218464 '], time:0.19254756ms
         out_f32x4: ['-0.05288643 ', '-0.14218464 '], time:0.19258785ms
        out_f32_th: ['-0.05288643 ', '-0.14218464 '], time:0.48660636ms
-------------------------------------------------------------------------------------
           out_f16: ['-0.052948   ', '-0.14221191 '], time:0.05689216ms
         out_f16x2: ['-0.052948   ', '-0.14221191 '], time:0.04335928ms
         out_f16x8: ['-0.052948   ', '-0.14221191 '], time:0.03096652ms
     out_f16x8pack: ['-0.052948   ', '-0.14221191 '], time:0.02706647ms
        out_f16_th: ['-0.05288696 ', '-0.14221191 '], time:0.05971408ms
-------------------------------------------------------------------------------------

```
