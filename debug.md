    
  ## 写程序和调试程序中出现过的不提示直接跑死matlab的问题集锦
  
  * Check failed: error == cudaSuccess (2 vs. 0) out of memory 
   使用　　nvidia-smi 　查看内存。
   由于用于图片的ＣＮＮ通常使用ＧＰＵ却不释放。造成ＧＰＵ显存占用过高。
   此时该程序用于视频中，必须在一次ＣＮＮ之后重置　ＧＰＵ
　  caffe.reset_all();
