# dependencies file

gclient_gn_args_file = 'src/build/config/gclient_args.gni'                                          
                                                                                                    
vars = {                                                                                            
  # By default, we should check out everything needed to run on the main                            
  # chromium waterfalls. More info at: crbug.com/570091.                                            
  'checkout_configuration': 'default',                                                              
  'checkout_instrumented_libraries': 'checkout_linux and checkout_configuration == "default"',      
  'chromium_revision': '4559b6b576fc5bd8f36ad7cde13bcf5215bec9dc',                                  
}                                                                                                   
                                                                                                    
deps = {
  'src/build':                                                                                      
    'https://chromium.googlesource.com/chromium/src/build@e1db346d5ddd59587fb3dd98dd85fb7ac07c2c00',
  'src/buildtools':                                                                                 
    'https://chromium.googlesource.com/chromium/src/buildtools@6302c1175607a436e18947a5abe9df2209e845fc',
    'src/buildtools/linux64': {                                                                       
    'packages': [                                                                                       
      {                                                                                             
        'package': 'gn/gn/linux-amd64',                                                             
        'version': 'git_revision:53d92014bf94c3893886470a1c7c1289f8818db0',                         
      }                                                                                             
    ],                                                                                              
    'dep_type': 'cipd',                                                                             
    'condition': 'checkout_linux',                                                                  
  },                                                                                                
  'src/buildtools/mac': {                                                                           
    'packages': [                                                                                   
      {                                                                                             
        'package': 'gn/gn/mac-amd64',                                                               
        'version': 'git_revision:53d92014bf94c3893886470a1c7c1289f8818db0',                         
      }                                                                                             
    ],                                                                                              
    'dep_type': 'cipd',                                                                             
    'condition': 'checkout_mac',                                                                    
  },                                                                                                
  'src/buildtools/win': {                                                                           
    'packages': [                                                                                   
      {                                                                                             
        'package': 'gn/gn/windows-amd64',                                                           
        'version': 'git_revision:53d92014bf94c3893886470a1c7c1289f8818db0',                         
      }                                                                                             
    ],                                                                                              
    'dep_type': 'cipd',                                                                             
    'condition': 'checkout_win',                                                                    
  },                                                                                                
                                                                                                    
  'src/buildtools/clang_format/script':                                                             
    'https://chromium.googlesource.com/chromium/llvm-project/cfe/tools/clang-format.git@96636aa0e9f047f17447f2d45a094d0b59ed7917',
  'src/buildtools/third_party/libc++/trunk':                                                        
    'https://chromium.googlesource.com/external/github.com/llvm/llvm-project/libcxx.git@d9040c75cfea5928c804ab7c235fed06a63f743a',
  'src/buildtools/third_party/libc++abi/trunk':                                                     
    'https://chromium.googlesource.com/external/github.com/llvm/llvm-project/libcxxabi.git@196ba1aaa8ac285d94f4ea8d9836390a45360533',
  'src/buildtools/third_party/libunwind/trunk':                                                     
    'https://chromium.googlesource.com/external/github.com/llvm/llvm-project/libunwind.git@d999d54f4bca789543a2eb6c995af2d9b5a1f3ed',
  'src/third_party/depot_tools':                                                                    
    'https://chromium.googlesource.com/chromium/tools/depot_tools.git@dc7b108da629de39f923d510fc76ea2f58efa521',
}

hooks = [
  # Pull clang-format binaries using checked-in hashes.                                             
  {                                                                                                 
    'name': 'clang_format_win',                                                                     
    'pattern': '.',                                                                                 
    'condition': 'host_os == "win"',                                                                
    'action': [ 'download_from_google_storage',                                                     
                '--no_resume',                                                                      
                '--platform=win32',                                                                 
                '--no_auth',                                                                        
                '--bucket', 'chromium-clang-format',                                                
                '-s', 'src/buildtools/win/clang-format.exe.sha1',                                   
    ],                                                                                              
  },                                                                                                
  {                                                                                                 
    'name': 'clang_format_mac',                                                                     
    'pattern': '.',                                                                                 
    'condition': 'host_os == "mac"',                                                                
    'action': [ 'download_from_google_storage',                                                     
                '--no_resume',                                                                      
                '--platform=darwin',                                                                
                '--no_auth',                                                                        
                '--bucket', 'chromium-clang-format',                                                
                '-s', 'src/buildtools/mac/clang-format.sha1',                                       
    ],                                                                                              
  },                                                                                                
  {                                                                                                 
    'name': 'clang_format_linux',                                                                   
    'pattern': '.',                                                                                 
    'condition': 'host_os == "linux"',                                                              
    'action': [ 'download_from_google_storage',                                                     
                '--no_resume',                                                                      
                '--platform=linux*',                                                                
                '--no_auth',                                                                        
                '--bucket', 'chromium-clang-format',                                                
                '-s', 'src/buildtools/linux64/clang-format.sha1',                                   
    ],                                                                                              
  },
]
