```

!wget -O animessl.zip https://example.com
!unzip animessl.zip -d animessl #csv


!pip install git+https://github.com/mlfoundations/open_clip.git
!git clone https://github.com/koke2c95/clip-retrieval-H.git
%cd clip-retrieval-H

%cd /content/clip-retrieval

!mkdir embeddings_folder
!python clip_retrieval/cli.py inference --clip_model open_clip:ViT-H-14 --input_dataset animessl --output_folder embeddings_folder

!python clip_retrieval/cli.py index embeddings_folder index_folder

#!zip -r openclipH_animessl.zip embeddings_folder/ index_folder/
#!rm -r embeddings_folder/ index_folder/
!zip -r openclipH_animessl.zip embeddings_folder/

#!clip-retrieval filter --query "chibi" --output_folder "test2/" --indice_folder index_folder ----num_results 3
# same dir mv
!python clip_retrieval/cli.py filter --query "girl book" --output_folder "./test2" --indice_folder index_folder ----num_results 9
!python make_img.py --recursive --path test2 --sort none --ratio 1 1 --size 256 --uneven
!rm test2/*

from IPython.display import clear_output
clear_output()
from IPython.display import Image
Image('result.jpg')

```
