codigo-matlab
=============
unction varargout = Interfaz(varargin)
gui_Singleton = 1;
gui_State = struct('gui_Name',       mfilename, ...
                   'gui_Singleton',  gui_Singleton, ...
                   'gui_OpeningFcn', @Interfaz_OpeningFcn, ...
                   'gui_OutputFcn',  @Interfaz_OutputFcn, ...
                   'gui_LayoutFcn',  [] , ...
                   'gui_Callback',   []);
if nargin && ischar(varargin{1})
    gui_State.gui_Callback = str2func(varargin{1});
end

if nargout
    [varargout{1:nargout}] = gui_mainfcn(gui_State, varargin{:});
else
    gui_mainfcn(gui_State, varargin{:});
end


function Interfaz_OpeningFcn(hObject, eventdata, handles, varargin)

handles.output = hObject;

guidata(hObject, handles);

;

function varargout = Interfaz_OutputFcn(hObject, eventdata, handles) 

varargout{1} = handles.output;


function funcion_activacion_Callback(hObject, eventdata, handles)
 val=get(handles.funcion_activacion,'Value');
 if(val==2)
  handles.funcion_seleccionada = 'hardlim';
  guidata(hObject,handles);
 else if(val==3)
     handles.handles.funcion_seleccionada = 'hardlims';
     guidata(hObject,handles);
     end
 end

function funcion_activacion_CreateFcn(hObject, eventdata, handles)
dato1=str2double(get(hObject,'String'));
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end

function x1d1_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end

function x1d2_CreateFcn(hObject, eventdata, handles)


if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end


function x1d3_Callback(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end

function x1d4_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end

function x2d4_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end


function x1d5_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end

function x2d1_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end

function x2d2_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end


function x2d3_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end

function calcular_Callback(hObject, eventdata, handles)

% MATRIZ DE ENTRADA 
d1 = str2num(get(handles.x1d1,'string'));
d2 = str2num(get(handles.x1d2,'string'));
d3 = str2num(get(handles.x1d3,'string'));
d4 = str2num(get(handles.x1d4,'string'));
d5 = str2num(get(handles.x1d5,'string'));
d6 = str2num(get(handles.x2d1,'string'));
d7 = str2num(get(handles.x2d2,'string'));
d8 = str2num(get(handles.x2d3,'string'));
d9 = str2num(get(handles.x2d4,'string'));
d10 = str2num(get(handles.x2d5,'string'));
d11 = str2num(get(handles.x3d1,'string'));
d12 = str2num(get(handles.x3d2,'string'));
d13 = str2num(get(handles.x3d3,'string'));
d14 = str2num(get(handles.x3d4,'string'));
d15 = str2num(get(handles.x3d5,'string'));
M = [d1 d2 d3 d4 d5; d6 d7 d8 d9 d10; d11 d12 d13 d14 d15];

% VECTOR 
d16 = str2num(get(handles.vv1,'string'));
d17 = str2num(get(handles.vv2,'string'));
d18 = str2num(get(handles.vv3,'string'));
d19 = str2num(get(handles.vv4,'string'));
d20 = str2num(get(handles.vv5,'string'));
V =  [d16 d17 d18 d19 d2];

 % OBTENER VALORES DE FUNCIONCIONES PROGRAMADAS
% obtener_funcion  = handles.funcion_seleccionada;
 obtener_entrenamiento = handles.entrenamiento_seleccionado;
 % OBTENER NEURONAS DE LAS CAPAS
  obtener_neuronas = handles.vector_neuronas;
 % OBTENER CAPAS
% obtener_capas = handles.num_cap;
% Crear la Red Neuronal
%Obtener Funcion harlim o harlims
 obtenerfuncionesh = handles.vectorff;
net = newff(minmax(M),obtener_neuronas,obtenerfuncionesh,obtener_entrenamiento);
% intervalo para ver resulatdos
net.trainParam.show=50;
%Taza de aprendizaje
net.trainParam.lr=0.04;
% numero de iteraciones
net.trainParam.spochs=100;
% error permitido
net.trainParam.goal= 1e-6;
Y = sim(net,M);
% net.IW(1);
% net.b(1);
plot(handles.grafica1,M,V,'b');
handles.visualizar_red = net;
guidata(hObject,handles);
 
 
 
function x1d3_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function grafica1_CreateFcn(hObject, eventdata, handles)


function aprendizaje_Callback(hObject, eventdata, handles)
 va=get(handles.funcion_activacion,'Value');
 if(va==2)
     handles.entrenamiento_seleccionado = 'trainbfg';
     guidata(hObject,handles);
 else if(va==3)
     handles.entrenamiento_seleccionado = 'trainbr';
     guidata(hObject,handles);
 else if(va==4)
     handles.entrenamiento_seleccionado = 'traincgb'; 
     guidata(hObject,handles);
     end
     end
 end



function aprendizaje_CreateFcn(hObject, eventdata, handles)
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end




% --- Executes on button press in limpiar.
function limpiar_Callback(hObject, eventdata, handles)
cla
set(handles.aprendizaje,'Enable','on');
 set(handles.funcion_activacion,'Enable','on');
 set(handles.aprendizaje,'Value',1);
 set(handles.funcion_activacion,'Value',1);
set(handles.x1d1,'String',' ');
 set(handles.x1d2,'String',' ');
 set(handles.x1d3,'String',' ');
 set(handles.x1d4,'String',' ');
 set(handles.x1d5,'String',' ');
 set(handles.x2d1,'String',' ');
 set(handles.x2d2,'String',' ');
 set(handles.x2d3,'String',' ');
 set(handles.x2d4,'String',' ');
 set(handles.x2d5,'String',' ');
 set(handles.x3d1,'String',' ');
 set(handles.x3d2,'String',' ');
 set(handles.x3d3,'String',' ');
 set(handles.x3d4,'String',' ');
 set(handles.x3d5,'String',' ');
 set(handles.num_capas,'String',' ');
 set(handles.capa1,'String',' ');
 set(handles.capa2,'String',' ');
 set(handles.capa3,'String',' ');
 set(handles.capa4,'String',' ');
 set(handles.capa5,'String',' ');
 set(handles.capa6,'String',' ');
 set(handles.capa7,'String',' ');
 set(handles.capa8,'String',' ');
 set(handles.capa9,'String',' ');
 set(handles.capa10,'String',' ');
 set(handles.vv1,'String',' ');
 set(handles.vv2,'String',' ');
 set(handles.vv3,'String',' ');
 set(handles.vv4,'String',' ');
 set(handles.vv5,'String',' ');
 set(handles.capa1,'Enable','off');
 set(handles.capa2,'Enable','off');
 set(handles.capa3,'Enable','off');
 set(handles.capa4,'Enable','off');
 set(handles.capa5,'Enable','off');
 set(handles.capa6,'Enable','off');
 set(handles.capa7,'Enable','off');
 set(handles.capa8,'Enable','off');
 set(handles.capa9,'Enable','off');
 set(handles.capa10,'Enable','off');


function num_capas_Callback(hObject, eventdata, handles)
numero_capas = str2num(get(handles.num_capas,'string'));
handles.num_cap = numero_capas;
guidata(hObject,handles);


function num_capas_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end




function x2d5_Callback(hObject, eventdata, handles)
% hObject    handle to x2d5 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)


% --- Executes during object creation, after setting all properties.
function x2d5_CreateFcn(hObject, eventdata, handles)
% hObject    handle to x2d5 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function x3d4_Callback(hObject, eventdata, handles)
% hObject    handle to x3d4 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)


function x3d4_CreateFcn(hObject, eventdata, handles)
% hObject    handle to x3d4 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function x3d1_Callback(hObject, eventdata, handles)
% hObject    handle to x3d1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)


function x3d1_CreateFcn(hObject, eventdata, handles)
% hObject    handle to x3d1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called


if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function x3d2_Callback(~, eventdata, handles)
% hObject    handle to x3d2 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)




% --- Executes during object creation, after setting all properties.
function x3d2_CreateFcn(hObject, eventdata, handles)
% hObject    handle to x3d2 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function x3d3_Callback(hObject, eventdata, handles)
% hObject    handle to x3d3 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)




% --- Executes during object creation, after setting all properties.
function x3d3_CreateFcn(hObject, eventdata, handles)
% hObject    handle to x3d3 (see GCBO)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function x3d5_Callback(hObject, eventdata, handles)
% hObject    handle to x3d5 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

function x3d5_CreateFcn(hObject, eventdata, handles)
% hObject    handle to x3d5 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function capa1_Callback(hObject, eventdata, handles)
% hObject    handle to capa1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)



% --- Executes during object creation, after setting all properties.
function capa1_CreateFcn(hObject, eventdata, handles)
% hObject    handle to capa1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end


% --- Executes on button press in Establecer.
function Establecer_Callback(hObject, eventdata, handles)
  valor=get(handles.funcion_activacion,'Value');
  valor1 = get(handles.aprendizaje,'Value');
    if(valor==1)&&(valor1==1)
        errordlg('Seleccione una Funcion y un Tipo de Aprendizaje','Error');
    else if (valor==2)&&(valor1==1)
        errordlg('Seleccione un Tipo de Aprendizaje','Error');
      else if (valor==3)&&(valor1==1)
        errordlg('Seleccione un Tipo de Aprendizaje','Error');
         else if (valor==1)&&(valor1==2)
        errordlg('Seleccione un Funcion de Activacion','Error');
       else if (valor==1)&&(valor1==3)
        errordlg('Seleccione un Funcion de Activacion','Error');
        else if (valor==1)&&(valor1==4)
        errordlg('Seleccione un Funcion de Activacion','Error');
       else if (valor==2)&&(valor1==2)
          set(handles.funcion_activacion,'Enable','off');
          set(handles.aprendizaje,'Enable','off');
         else if (valor==2)&&(valor1==3)
          set(handles.funcion_activacion,'Enable','off');
          set(handles.aprendizaje,'Enable','off'); 
          else if (valor==2)&&(valor1==4)
          set(handles.funcion_activacion,'Enable','off');
          set(handles.aprendizaje,'Enable','off');
          else if (valor==3)&&(valor1==2)
          set(handles.funcion_activacion,'Enable','off');
          set(handles.aprendizaje,'Enable','off');
          else if (valor==3)&&(valor1==3)
          set(handles.funcion_activacion,'Enable','off');
          set(handles.aprendizaje,'Enable','off');
          else if (valor==3)&&(valor1==4)
          set(handles.funcion_activacion,'Enable','off');
          set(handles.aprendizaje,'Enable','off');
           end
             end
          end
        end
    end
        end
            end
           end
             end
          end
        end
    end
        
% --- Executes on button   s in pushbutton7.
function pushbutton7_Callback(hObject, eventdata, handles)
 nc = str2num(get(handles.num_capas,'String'));
   if(nc ==1)
       set(handles.capa1, 'Enable','on');
       set(handles.capa2, 'Enable','off');
       set(handles.capa3, 'Enable','off');
       set(handles.capa4, 'Enable','off');
       set(handles.capa5, 'Enable','off');
       set(handles.capa6, 'Enable','off');
       set(handles.capa7, 'Enable','off');
       set(handles.capa8, 'Enable','off');
       set(handles.capa9, 'Enable','off');
       set(handles.capa10, 'Enable','off');
       else if(nc ==2)
       set(handles.capa1, 'Enable','on');
       set(handles.capa2, 'Enable','on');
       set(handles.capa3, 'Enable','off');
       set(handles.capa4, 'Enable','off');
       set(handles.capa5, 'Enable','off');
       set(handles.capa6, 'Enable','off');
       set(handles.capa7, 'Enable','off');
       set(handles.capa8, 'Enable','off');
       set(handles.capa9, 'Enable','off');
       set(handles.capa10, 'Enable','off');
   else if(nc ==3)
       set(handles.capa1, 'Enable','on');
       set(handles.capa2, 'Enable','on');
       set(handles.capa3, 'Enable','on');
       set(handles.capa4, 'Enable','off');
       set(handles.capa5, 'Enable','off');
       set(handles.capa6, 'Enable','off');
       set(handles.capa7, 'Enable','off');
       set(handles.capa8, 'Enable','off');
       set(handles.capa9, 'Enable','off');
       set(handles.capa10, 'Enable','off');
   else if(nc ==4)
       set(handles.capa1, 'Enable','on');
       set(handles.capa2, 'Enable','on');
       set(handles.capa3, 'Enable','on');
       set(handles.capa4, 'Enable','on');
       set(handles.capa5, 'Enable','off');
       set(handles.capa6, 'Enable','off');
       set(handles.capa7, 'Enable','off');
       set(handles.capa8, 'Enable','off');
       set(handles.capa9, 'Enable','off');
       set(handles.capa10, 'Enable','off');
   else if(nc ==5)
       set(handles.capa1, 'Enable','on');
       set(handles.capa2, 'Enable','on');
       set(handles.capa3, 'Enable','on');
       set(handles.capa4, 'Enable','on');
       set(handles.capa5, 'Enable','on');
       set(handles.capa6, 'Enable','off');
       set(handles.capa7, 'Enable','off');
       set(handles.capa8, 'Enable','off');
       set(handles.capa9, 'Enable','off');
       set(handles.capa10, 'Enable','off');
   else if(nc ==6)
       set(handles.capa1, 'Enable','on');
       set(handles.capa2, 'Enable','on');
       set(handles.capa3, 'Enable','on');
       set(handles.capa4, 'Enable','on');
       set(handles.capa5, 'Enable','on');
       set(handles.capa6, 'Enable','on');
       set(handles.capa7, 'Enable','off');
       set(handles.capa8, 'Enable','off');
       set(handles.capa9, 'Enable','off');
       set(handles.capa10, 'Enable','off');
   else if(nc ==7)
       set(handles.capa1, 'Enable','on');
       set(handles.capa2, 'Enable','on');
       set(handles.capa3, 'Enable','on');
       set(handles.capa4, 'Enable','on');
       set(handles.capa5, 'Enable','on');
       set(handles.capa6, 'Enable','on');
       set(handles.capa7, 'Enable','on');
       set(handles.capa8, 'Enable','off');
       set(handles.capa9, 'Enable','off');
       set(handles.capa10, 'Enable','off');
   else if(nc ==8)
       set(handles.capa1, 'Enable','on'); 
       set(handles.capa2, 'Enable','on');
       set(handles.capa3, 'Enable','on');
       set(handles.capa4, 'Enable','on');
       set(handles.capa5, 'Enable','on');
       set(handles.capa6, 'Enable','on');
       set(handles.capa7, 'Enable','on');
       set(handles.capa8, 'Enable','on');
       set(handles.capa9, 'Enable','off');
       set(handles.capa10, 'Enable','off');
   else if(nc ==9)
       set(handles.capa1, 'Enable','on');
       set(handles.capa2, 'Enable','on');
       set(handles.capa3, 'Enable','on');
       set(handles.capa4, 'Enable','on');
       set(handles.capa5, 'Enable','on');
       set(handles.capa6, 'Enable','on');
       set(handles.capa7, 'Enable','on');
       set(handles.capa8, 'Enable','on');
       set(handles.capa9, 'Enable','on');
       set(handles.capa10, 'Enable','off');
   else if(nc ==10)
       set(handles.capa1, 'Enable','on');
       set(handles.capa2, 'Enable','on');
       set(handles.capa3, 'Enable','on');
       set(handles.capa4, 'Enable','on');
       set(handles.capa5, 'Enable','on');
       set(handles.capa6, 'Enable','on');
       set(handles.capa7, 'Enable','on');
       set(handles.capa8, 'Enable','on');
       set(handles.capa9, 'Enable','on');
       set(handles.capa10, 'Enable','on');

       end
       end
       end
       end
       end
       end
       end
       end
       end
   end



function capa2_Callback(hObject, eventdata, handles)

function capa2_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function capa3_Callback(hObject, eventdata, handles)

function capa3_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function capa4_Callback(hObject, eventdata, handles)

function capa4_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function capa5_Callback(hObject, eventdata, handles)

function capa5_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function capa6_Callback(hObject, eventdata, handles)

function capa6_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function capa7_Callback(hObject, eventdata, handles)

function capa7_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function capa8_Callback(hObject, eventdata, handles)

function capa8_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function capa9_Callback(hObject, eventdata, handles)


function capa9_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function capa10_Callback(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end


function vv1_Callback(hObject, eventdata, handles)

function vv1_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function vv2_Callback(hObject, eventdata, handles)

function vv2_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function vv3_Callback(hObject, eventdata, handles)

function vv3_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function vv4_Callback(hObject, eventdata, handles)

function vv4_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function vv5_Callback(hObject, eventdata, handles)


function vv5_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end


function calcular_CreateFcn(hObject, eventdata, handles)

function reestablecer_Callback(hObject, eventdata, handles)
set(handles.funcion_activacion,'Enable','on');
          set(handles.aprendizaje,'Enable','on');



function grabar_neuronas_Callback(hObject, eventdata, handles)
d21 = str2num(get(handles.num_capas,'string'));
vector_capas=[];
vec=[];
obtener_funcion  = handles.funcion_seleccionada;
 if(d21 ==1)
       nnc1 = str2num(get(handles.capa1,'string'));
       vector_capas =[nnc1];
       set(handles.capa1, 'Enable','off');
      if obtener_funcion=='hardlim';
          vec= {'hardlim'};
      else if obtener_funcion=='hardlims';
              vec= {'hardlims'}
     end   
      end          
 else if(d21==2)
         nnc1 = str2num(get(handles.capa1,'string'));
         nnc2 = str2num(get(handles.capa2,'string'));
         vector_capas =[nnc1 nnc2];
         set(handles.capa1, 'Enable','off');
         set(handles.capa2, 'Enable','off');
          if (obtener_funcion== 'hardlim');
          vec= {'hardlim' 'hardlim'};
      else if obtener_funcion=='hardlims';
              vec= {'hardlims' 'hardlims'}
     end  
        end     
     else if(d21==3)
         nnc1 = str2num(get(handles.capa1,'string'));
         nnc2 = str2num(get(handles.capa2,'string'));
         nnc3 = str2num(get(handles.capa3,'string'));
         vector_capas =[nnc1 nnc2 nnc3];
         set(handles.capa1, 'Enable','off');
         set(handles.capa2, 'Enable','off');
         set(handles.capa3, 'Enable','off');
           if (obtener_funcion=='hardlim');
          vec= {'hardlim' 'hardlim' 'hardlim'};
      else if obtener_funcion=='hardlims';
              vec= {'hardlims' 'hardlims' 'hardlims'}
     end  
        end 
    else if(d21==4)
         nnc1 = str2num(get(handles.capa1,'string'));
         nnc2 = str2num(get(handles.capa2,'string'));
         nnc3 = str2num(get(handles.capa3,'string'));
         nnc4 = str2num(get(handles.capa4,'string'));
         vector_capas =[nnc1 nnc2 nnc3 nnc4];
         set(handles.capa1, 'Enable','off');
         set(handles.capa2, 'Enable','off');
         set(handles.capa3, 'Enable','off');
         set(handles.capa4, 'Enable','off');
           if (obtener_funcion=='hardlim');
          vec= {'hardlim' 'hardlim' 'hardlim' 'hardlim'};
      else if obtener_funcion=='hardlims';
              vec= {'hardlims' 'hardlims' 'hardlims' 'hardlims'}
     end  
        end 
    else if(d21==5)
         nnc1 = str2num(get(handles.capa1,'string'));
         nnc2 = str2num(get(handles.capa2,'string'));
         nnc3 = str2num(get(handles.capa3,'string'));
         nnc4 = str2num(get(handles.capa4,'string'));
         nnc5 = str2num(get(handles.capa5,'string'));
         vector_capas =[nnc1 nnc2 nnc3 nnc4 nnc5]; 
         set(handles.capa1, 'Enable','off');
         set(handles.capa2, 'Enable','off');
         set(handles.capa3, 'Enable','off');
         set(handles.capa4, 'Enable','off');
         set(handles.capa5, 'Enable','off');
          if (obtener_funcion=='hardlim');
          vec= {'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim'};
      else if obtener_funcion=='hardlims';
          vec= {'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims'}
          end
        end
    else if(d21==6)
         nnc1 = str2num(get(handles.capa1,'string'));
         nnc2 = str2num(get(handles.capa2,'string'));
         nnc3 = str2num(get(handles.capa3,'string'));
         nnc4 = str2num(get(handles.capa4,'string'));
         nnc5 = str2num(get(handles.capa5,'string'));
         nnc6 = str2num(get(handles.capa56,'string'));
         vector_capas=[nnc1 nnc2 nnc3 nnc4 nnc5 nnc6];
         set(handles.capa1, 'Enable','off');
         set(handles.capa2, 'Enable','off');
         set(handles.capa3, 'Enable','off');
         set(handles.capa4, 'Enable','off');
         set(handles.capa5, 'Enable','off');
         set(handles.capa6, 'Enable','off');
             if (obtener_funcion=='hardlim');
          vec= {'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim'};
      else if obtener_funcion=='hardlims';
          vec= {'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims'}
          end
        end
 else if(d21==7)
         nnc1 = str2num(get(handles.capa1,'string'));
         nnc2 = str2num(get(handles.capa2,'string'));
         nnc3 = str2num(get(handles.capa3,'string'));
         nnc4 = str2num(get(handles.capa4,'string'));
         nnc5 = str2num(get(handles.capa5,'string'));
         nnc6 = str2num(get(handles.capa6,'string'));
         nnc7 = str2num(get(handles.capa7,'string'));
         vector_capas=[nnc1 nnc2 nnc3 nnc4 nnc5 nnc6 nnc7];
         set(handles.capa1, 'Enable','off');
         set(handles.capa2, 'Enable','off');
         set(handles.capa3, 'Enable','off');
         set(handles.capa4, 'Enable','off');
         set(handles.capa5, 'Enable','off');
         set(handles.capa6, 'Enable','off');
         set(handles.capa7, 'Enable','off');
            if (obtener_funcion=='hardlim');
          vec= {'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim'};
      else if obtener_funcion=='hardlims';
          vec= {'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims'}
          end
        end
else if(d21==8)
         nnc1 = str2num(get(handles.capa1,'string'));
         nnc2 = str2num(get(handles.capa2,'string'));
         nnc3 = str2num(get(handles.capa3,'string'));
         nnc4 = str2num(get(handles.capa4,'string'));
         nnc5 = str2num(get(handles.capa5,'string'));
         nnc6 = str2num(get(handles.capa6,'string'));
         nnc7 = str2num(get(handles.capa7,'string'));
         nnc8 = str2num(get(handles.capa8,'string'));
         vector_capas=[nnc1 nnc2 nnc3 nnc4 nnc5 nnc6 nnc7 nnc8];
         set(handles.capa1, 'Enable','off');
         set(handles.capa2, 'Enable','off');
         set(handles.capa3, 'Enable','off');
         set(handles.capa4, 'Enable','off');
         set(handles.capa5, 'Enable','off');
         set(handles.capa6, 'Enable','off');
         set(handles.capa7, 'Enable','off');
         set(handles.capa8, 'Enable','off'); 
           if (obtener_funcion=='hardlim');
          vec= {'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim'};
      else if obtener_funcion=='hardlims';
          vec= {'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims' }
          end
        end
else if(d21==9)
         nnc1 = str2num(get(handles.capa1,'string'));
         nnc2 = str2num(get(handles.capa2,'string'));
         nnc3 = str2num(get(handles.capa3,'string'));
         nnc4 = str2num(get(handles.capa4,'string'));
         nnc5 = str2num(get(handles.capa5,'string'));
         nnc6 = str2num(get(handles.capa6,'string'));
         nnc7 = str2num(get(handles.capa7,'string'));
         nnc8 = str2num(get(handles.capa8,'string'));
         nnc9 = str2num(get(handles.capa9,'string'));
         vector_capas=[nnc1 nnc2 nnc3 nnc4 nnc5 nnc6 nnc7 nnc8 nnc9];
         set(handles.capa1, 'Enable','off');
         set(handles.capa2, 'Enable','off');
         set(handles.capa3, 'Enable','off');
         set(handles.capa4, 'Enable','off');
         set(handles.capa5, 'Enable','off');
         set(handles.capa6, 'Enable','off');
         set(handles.capa7, 'Enable','off');
         set(handles.capa8, 'Enable','off'); 
         set(handles.capa8, 'Enable','off'); 
         if (obtener_funcion=='hardlim');
          vec= {'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim'};
      else if obtener_funcion=='hardlims';
          vec= {'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims'}
          end
        end
 else if(d21==10)
         nnc1 = str2num(get(handles.capa1,'string'));
         nnc2 = str2num(get(handles.capa2,'string'));
         nnc3 = str2num(get(handles.capa3,'string'));
         nnc4 = str2num(get(handles.capa4,'string'));
         nnc5 = str2num(get(handles.capa5,'string'));
         nnc6 = str2num(get(handles.capa6,'string'));
         nnc7 = str2num(get(handles.capa7,'string'));
         nnc8 = str2num(get(handles.capa8,'string'));
         nnc9 = str2num(get(handles.capa9,'string'));
         nnc10 = str2num(get(handles.capa10,'string'));
         vector_capas=[nnc1 nnc2 nnc3 nnc4 nnc5 nnc6 nnc7 nnc8 nnc9 nnc10];
           if (obtener_funcion=='hardlim');
          vec= {'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim' 'hardlim'};
      else if obtener_funcion=='hardlims';
          vec= {'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims' 'hardlims'}
          end
        end
     end
    end
    end
     end
        end
        end
        end
         end
     end
 end
 
  handles.vector_neuronas = vector_capas;
   guidata(hObject,handles);
   handles.vectorff = vec;
    guidata(hObject,handles);



function pushbutton11_Callback(hObject, eventdata, handles)




function ver_red_Callback(hObject, eventdata, handles)
ver_neurona = handles.visualizar_red;
view(ver_neurona);



function capa10_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function x1d4_Callback(hObject, eventdata, handles)
% hObject    handle to x1d4 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)





function x1d5_Callback(hObject, eventdata, handles)
% hObject    handle to x1d5 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)



function x1d2_Callback(hObject, eventdata, handles)
% hObject    handle to x1d2 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

 
function x1d1_Callback(hObject, eventdata, handles)
% hObject    handle to x1d1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)




function x2d3_Callback(hObject, eventdata, handles)
% hObject    handle to x2d3 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)



function x2d4_Callback(hObject, eventdata, handles)
% hObject    handle to x2d4 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)




function x2d2_Callback(hObject, eventdata, handles)
% hObject    handle to x2d2 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

   function x2d1_Callback(hObject, eventdata, handles)
% hObject    handle to x2d1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)



% --- Executes on button press in desacer.
function desacer_Callback(hObject, eventdata, handles)
set(handles.capa1, 'String','');
set(handles.capa2, 'String','');
set(handles.capa3, 'String','');
set(handles.capa4, 'String','');
set(handles.capa5, 'String','');
set(handles.capa6, 'String','');
set(handles.capa7, 'String','');
set(handles.capa8, 'String','');
set(handles.capa9, 'String','');
set(handles.capa10, 'String','');



