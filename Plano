# importing the module 
import cv2
import numpy as np

listax = []
listay = []
dimenciones = None
   
# function to display the coordinates of 
# of the points clicked on the image  
def click_event(event, x, y, flags, params): 
    
    global listax
    global listay
    global dimenciones

    # checking for left mouse clicks
    if event == cv2.EVENT_LBUTTONDOWN:
        
        x1 = int(x/3)
        y1 = 100- int(y/3)

        listax.append(x1)
        listay.append(y1)
        # displaying the coordinates 
        # on the Shell 
        print(x1, ' ', y1)
  
        # displaying the coordinates 
        # on the image window 
        font = cv2.FONT_HERSHEY_SIMPLEX 
        cv2.putText(img, str(len(listax)-1), (x,y), font, 
                    1, (255, 0, 0), 2) 
        cv2.imshow('image', img) 
  
# driver function 
if __name__=="__main__": 
  
    # reading the image 
    img = cv2.imread('PLANO_3.png',1) 

    # displaying the image 
    cv2.imshow('image', img)
    dimenciones = img.shape
  
    # setting mouse handler for the image 
    # and calling the click_event() function 
    
    cv2.setMouseCallback('image', click_event)

    # wait for a key to be pressed to exit 
    cv2.waitKey(0) 
  
    # close the window 
    cv2.destroyAllWindows() 

    A = np.zeros((len(listax),len(listay)))
    print("Cantidad de nodos: ",len(listax))

    if len(listax)>0:
        op = True
        while op:
            conec = input("Desea agregar una conexión? S/N : ")
            if conec.upper() == "S":
                inicial = int(input("Coloque el nodo inicial: "))
                final = int(input("Coloque el nodo final: "))
                A[inicial][final] = 1
                A[final][inicial] = 1
                print(f"Se establecio conexion del nodo {inicial} con el nodo {final}")
            elif conec.upper() == "N":
                op = False


    print()
    print("\t\t Distancias")
    for i in range(len(listax)):
        for j in range(len(listay)):
            if A[i][j] == 1:
                dist = ((listax[i]-listax[j])**2 + (listay[i]-listay[j])**2)**(1/2)
                print(f"La distancia del nodo {i} al nodo {j} es = {dist:9.2f}")
                A[i][j] = dist
                A[j][i] = dist
    
    print()
    print("\tMatriz de adyacencia")
    for i in range(len(listax)):
        for j in range(len(listay)):
            print(f"{A[i][j]:9.2f}",end=" ")
        print()
    input()
