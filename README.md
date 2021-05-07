# UTSPengolahancitra

![uts1](https://user-images.githubusercontent.com/56390857/117509425-6c3f6480-afb4-11eb-8a88-a1ad89eb0094.PNG)
![uts2](https://user-images.githubusercontent.com/56390857/117509428-6e092800-afb4-11eb-8cd9-21eaac137f3f.PNG)


sintag :
![Capture](https://user-images.githubusercontent.com/56390857/117509899-42d30880-afb5-11eb-950f-6a723f07277b.PNG)


![uts3](https://user-images.githubusercontent.com/56390857/117509853-2a62ee00-afb5-11eb-951c-1861d9d16270.PNG)


function varargout = UTS(varargin)
% UTS MATLAB code for UTS.fig
%      UTS, by itself, creates a new UTS or raises the existing
%      singleton*.
%
%      H = UTS returns the handle to a new UTS or the handle to
%      the existing singleton*.
%
%      UTS('CALLBACK',hObject,eventData,handles,...) calls the local
%      function named CALLBACK in UTS.M with the given input arguments.
%
%      UTS('Property','Value',...) creates a new UTS or raises the
%      existing singleton*.  Starting from the left, property value pairs are
%      applied to the GUI before UTS_OpeningFcn gets called.  An
%      unrecognized property name or invalid value makes property application
%      stop.  All inputs are passed to UTS_OpeningFcn via varargin.
%
%      *See GUI Options on GUIDE's Tools menu.  Choose "GUI allows only one
%      instance to run (singleton)".
%
% See also: GUIDE, GUIDATA, GUIHANDLES
% Edit the above text to modify the response to help UTS
% Last Modified by GUIDE v2.5 06-May-2021 12:11:36
% Begin initialization code - DO NOT EDIT
gui_Singleton = 1;
gui_State = struct('gui_Name',       mfilename, ...
                   'gui_Singleton',  gui_Singleton, ...
                   'gui_OpeningFcn', @UTS_OpeningFcn, ...
                   'gui_OutputFcn',  @UTS_OutputFcn, ...
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
% End initialization code - DO NOT EDIT
% --- Executes just before UTS is made visible.
function UTS_OpeningFcn(hObject, eventdata, handles, varargin)
% This function has no output args, see OutputFcn.
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
% varargin   command line arguments to UTS (see VARARGIN)
% Choose default command line output for UTS
handles.output = hObject;
% Update handles structure
guidata(hObject, handles);
% UIWAIT makes UTS wait for user response (see UIRESUME)
% uiwait(handles.figure1);
% --- Outputs from this function are returned to the command line.
function varargout = UTS_OutputFcn(hObject, eventdata, handles) 
% varargout  cell array for returning output args (see VARARGOUT);
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
% Get default command line output from handles structure
varargout{1} = handles.output;
% --- Executes on button press in pushbutton1.
function pushbutton1_Callback(hObject, eventdata, handles)
% hObject    handle to pushbutton1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

[filename, pathname] = uigetfile({'*.jpg','*.png'});
img = imread([pathname,filename]);
axes(handles.axes1);
imshow(img);

R = img(:,:,1);
G = img(:,:,2);
B = img(:,:,3);

Red = cat(3,R,G*0,B*0);
Green = cat(3,R*0,G,B*0);
Blue = cat(3,R*0,G*0,B);

axes(handles.axes2);
imshow(Red);
title('Merah');
axes(handles.axes3);
histogram(Red(:),256);
set(gca,'XLim',[0 255]);
set(gca,'YLim',[0 15000]);
grid on

axes(handles.axes4);
imshow(Green);
title('Hijau');
axes(handles.axes5);
histogram(Green(:),256);
set(gca,'XLim',[0 255]);
set(gca,'YLim',[0 15000]);
grid on

axes(handles.axes6);
imshow(Blue);
title('Biru');
axes(handles.axes7);
histogram(Blue(:),256);
set(gca,'XLim',[0 255]);
set(gca,'YLim',[0 15000
grid on
