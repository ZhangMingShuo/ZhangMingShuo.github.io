### Asp.NetCore 2.1 使用AutoMapper自动映射转换实体 DTO，Data2ViewModel  
#### 工具包
######  AutoMapper.Extensions.Microsoft.DependencyInjection
#### 项目目录
![image](https://note.youdao.com/yws/api/personal/file/B898BC177FD0470A88E0D4329F5858BC?method=download&shareKey=c4c15e3636ac72561245e1c562f026eb)

#### 接口调试
![image](https://note.youdao.com/yws/api/personal/file/8A6A57871CF447AB9F9B868B8261EEE5?method=download&shareKey=b3bf37d752104f65df1b66e67e060718)

#### Program.cs

```CSharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.AspNetCore;
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.Logging;

namespace WebApp
{
    public class Program
    {
        public static void Main(string[] args)
        {
            CreateWebHostBuilder(args).Build().Run();
        }

        public static IWebHostBuilder CreateWebHostBuilder(string[] args) =>
            WebHost.CreateDefaultBuilder(args)
                .UseStartup<Startup>();
    }
}

```

#### Startup.cs
```CSharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.HttpsPolicy;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using Microsoft.Extensions.Options;
using AutoMapper;
namespace WebApp
{
    public class Startup
    {
        public Startup(IConfiguration configuration)
        {
            Configuration = configuration;
        }

        public IConfiguration Configuration { get; }

        // This method gets called by the runtime. Use this method to add services to the container.
        public void ConfigureServices(IServiceCollection services)
        {
            services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
            
            services.AddAutoMapper(c => c.AddProfile(new AutoMapperHelper.AutoMapperProfile()));
            
        }

        // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
        public void Configure(IApplicationBuilder app, IHostingEnvironment env)
        {
            if (env.IsDevelopment())
            {
                app.UseDeveloperExceptionPage();
            }
            else
            {
                app.UseHsts();
            }

            app.UseHttpsRedirection();
            app.UseMvc();
        }
    }
}

```
#### SendMsg.cs  
```CSharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace WebApp.AutoMapperTestModel
{
    public class SendMsg
    {
        public int mid { get; set; }
        public string mTitle { get; set;}
        public string mContent { get; set;}
        public DateTime editTime { get; set; }
    }
}
```


#### SendMsgViewModel.cs
```CSharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace WebApp.AutoMapperTestModel
{
    public class SendMsgViewModel
    {
        public int mid { get; set; }
        public string mTitlw { get; set; }
        public string mContent { get; set; }
        public DateTime UpdateTime { get; set; }
    }
}
```

#### DoAutoMapperController.cs
```CSharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace WebApp.Controllers
{
    using WebApp.AutoMapperTestModel;
    using AutoMapper;
    using Microsoft.AspNetCore.Mvc;
    [ApiController]
    [Route("api/[Controller]")]
    public class DoAutoMapperController:ControllerBase
    {
        private IMapper _mapper;
        private List<SendMsg> sendMsgList { get; set; }
        private SendMsg sendMsgOne { get; set; }

        public DoAutoMapperController(IMapper mapper)
        {
            _mapper = mapper;
            sendMsgList = GetList();
            sendMsgOne = GetSendMsg();
        }
        private List<SendMsg> GetList()
        {
            return new List<SendMsg> {
                 new SendMsg{ mid=110,editTime=DateTime.Parse("1998-01-01"),mContent="你好我好大家好1",mTitle="T1"},
                 new SendMsg{ mid=111,editTime=DateTime.Parse("1998-02-01"),mContent="你好我好大家好2",mTitle="T2"},
                 new SendMsg{ mid=112,editTime=DateTime.Parse("1998-03-01"),mContent="你好我好大家好3",mTitle="T3"},
                 new SendMsg{ mid=113,editTime=DateTime.Parse("1998-04-01"),mContent="你好我好大家好4",mTitle="T4"},
                 new SendMsg{ mid=114,editTime=DateTime.Parse("1998-05-01"),mContent="你好我好大家好5",mTitle="T5"}
            };
        }

        private SendMsg GetSendMsg()
        {
            return new SendMsg { mid = 110, editTime = DateTime.Parse("1998-01-01"), mContent = "你好我好大家好1", mTitle = "T1" };
        }


        [HttpGet("Automapper")]
        public ActionResult<SendMsgViewModel> AutomapperOne()
        {
            SendMsgViewModel sendmsg = _mapper.Map<SendMsg, SendMsgViewModel>(sendMsgOne);
            if (sendmsg == null)
            {
                return NotFound();
            }
            return sendmsg;
        }

        [HttpGet("AutomapperList")]
        public ActionResult<List<SendMsgViewModel>> AutomapperList()
        {
            List<SendMsgViewModel> sendMsgViewModels = 
                _mapper.Map<List<SendMsg>, List<SendMsgViewModel>>(sendMsgList);
            if (sendMsgViewModels == null )
            {
                return NotFound();
            }
            return sendMsgViewModels;

        }
     
    }
}
```

#### AutoMapperHelper.cs
```CSharp
using AutoMapper;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace WebApp.AutoMapperHelper
{
    public class AutoMapperHelper
    {
        private static MapperConfiguration config;
        public AutoMapperHelper()
        {
            config = new MapperConfiguration(c => c.AddProfile<AutoMapperProfile>());
        }
    }
}

```

#### AutoMapperProfile.cs
```CSharp
using AutoMapper;
using WebApp.AutoMapperTestModel;

namespace WebApp.AutoMapperHelper
{
    public class AutoMapperProfile:Profile
    {
        public AutoMapperProfile()
        {
            IMappingExpression<SendMsg, SendMsgViewModel> mappingExpression = CreateMap<SendMsg, SendMsgViewModel>();
            mappingExpression.ForMember(des => des.UpdateTime, mem => mem.MapFrom(c => c.editTime))
                             .ForMember(des => des.mTitlw, mem => mem.MapFrom(c => c.mTitle));
        }
    }
}
```