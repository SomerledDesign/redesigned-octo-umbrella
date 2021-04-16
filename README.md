# redesigned-octo-umbrella
Steves



Plug 'tpope/vim-sensible'
Plug 'tpope/vim-fugitive'
Plug 'easymotion/vim-easymotion'
"Plug 'altercation/vim-colors-solarized' "Replaced by NeoSolarized
"Plug 'iCyMind/NeoSolarized'  "Disabled to test Dracula
Plug 'dracula/vim', { 'as': 'dracula' }
Plug 'Shougo/deoplete.nvim', { 'do': ':UpdateRemotePlugins' }
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'
Plug 'scrooloose/nerdcommenter'
"Plug 'sjl/gundo.vim'
Plug 'mbbill/undotree'
Plug 'Steve-V/vim-autocorrect'
Plug 'tmhedberg/SimpylFold'
Plug 'kshenoy/vim-signature'
"Plug 'junegunn/vim-peekaboo' " #buggy! not sure why
Plug 'freitass/todo.txt-vim'
call plug#end()



" NOTE: use call AutoCorrect() to activate autocorrect

" Use Dracula
  colorscheme dracula
    
" Use deoplete
  let g:deoplete#enable_at_startup = 1
" Use smartcase
  "let g:deoplete#enable_smart_case = 1
  call deoplete#custom#option('smart_case', v:true)

" <BS>: close popup and delete backword char
  inoremap <expr><BS>  deoplete#smart_close_popup()."\<C-h>"

" <CR>: close popup and save indent
  inoremap <silent> <CR> <C-r>=<SID>my_cr_function()<CR>
  function! s:my_cr_function() abort
    return deoplete#close_popup() . "\<CR>"
endfunction<Paste>

  "use deoplete with tab
  inoremap <expr><tab> pumvisible() ? "\<c-n>" : "\<tab>"

" Enable airline / powerline
set laststatus=2
set encoding=utf-8
"let g:airline_powerline_fonts = 1
let g:airline_powerline_fonts = 0 "let's try this for now, see if it fixes ssh
let g:airline#extensions#tabline#enabled = 1
let g:airline_theme = 'solarized'



" move by visual line rather than hard line
" essentially that way you dont have to scroll
" backwards when a line wraps

nnoremap j gj
nnoremap k gk




" create easier save commands (including quicksave!)
nnoremap <leader>ww :w<CR>
nnoremap <F5> :w<CR>
  
  
  " map space and backspace to scroll
nnoremap <SPACE> 10jzz
nnoremap <BS> 10kzz

" modern-style full-word backspace
inoremap <c-bs> <c-w>
set backspace=indent,eol,start
  
  " shrink tabs
set tabstop=2 softtabstop=2 expandtab shiftwidth=2 smarttab

" match parenthesis
set showmatch
highlight MatchParen ctermbg=lightblue 
set matchpairs+=<:>

let g:EasyMotion_do_mapping = 1 " Disable default mappings

" Bi-directional find motion
" Jump to anywhere you want with minimal keystrokes, with just one key binding.
" `s{char}{label}`
nmap <CR> <Plug>(easymotion-s)
" or
" `s{char}{char}{label}`
" Need one more keystroke, but on average, it may be more comfortable.
" nmap <CR> <Plug>(easymotion-s2)

" Turn on case sensitive and smart symbols feature
let g:EasyMotion_smartcase = 1
let g:EasyMotion_use_smartsign_us = 1


" make wrapping work as expected
set wrap linebreak nolist textwidth=0 wrapmargin=0 breakindent

" allow changing away from a modified buffer
set hidden
