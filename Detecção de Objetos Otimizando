import subprocess
import cv2
import numpy as np
import tkinter as tk
from tkinter import filedialog

class Teste:
    def __init__(self) -> None:
        pass
        def nvidia_teste():
            result = subprocess.run(["nvidia-smi"], capture_output=True, text=True)
            if result.returncode == 0:
                print("Saída do comando:")
                print(result.stdout)
            else:
                print("Erro ao executar o comando.")
                print("Saída de erro:")
                print(result.stderr)

        def darknet_start():    
            darknet_path = '/home/julian/darknet'    
            result = subprocess.run(['make'], cwd=darknet_path, capture_output=True, text=True)
            if result.returncode == 0:
                print('Compilação bem-sucedida!')
            else:
                print('Erro ao compilar:')
                print(result.stderr)
        def processar_imagem(imagem_path):
            command = f"./darknet detector test ./cfg/coco.data ./cfg/yolov4.cfg ./yolov4.weights {imagem_path} -i 0 -thresh 0.25"
            
            result = subprocess.run(command, shell=True, capture_output=True, text=True)

            if result.returncode == 0:
                print("Saída do comando:")
                print(result.stdout)
            else:
                print("Erro ao executar o comando.")
                print("Saída de erro:")
                print(result.stderr)

        def processar_video(video_path):
            command = f"./darknet detector demo ./cfg/coco.data ./cfg/yolov4.cfg ./yolov4.weights {video_path} -i 0 -thresh 0.25"
            
            result = subprocess.run(command, shell=True, capture_output=True, text=True)

            if result.returncode == 0:
                print("Saída do comando:")
                print(result.stdout)
            else:
                print("Erro ao executar o comando.")
                print("Saída de erro:")
                print(result.stderr)

        def escolher_arquivo():
            root = tk.Tk()
            root.withdraw()

            file_path = filedialog.askopenfilename()
            return file_path

        def teste_img_video():
            print("Escolha 1 para processar uma imagem ou 2 para processar um vídeo:")
            escolha = input()

            if escolha == "1":
                imagem_path = escolher_arquivo()
                processar_imagem(imagem_path)
            elif escolha == "2":
                video_path = escolher_arquivo()
                processar_video(video_path)
            else:
                print("Escolha errada, digite 1 ou 2!")

        # Chamando as funções
        nvidia_teste()
        darknet_start()
        teste_img_video()

app = Teste()
