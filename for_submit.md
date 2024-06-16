# for submit

## JS

```
  import React, {useState, useEffect} from 'react'
  import Swal from 'sweetalert2';
  // -------------input variables-----------


  const [languageData, setLanguageData] = useState({
    languageId: '',
    lcid: '',
    codepage: '',
    locale: '',
    languageName: '',
    localLanguageName: '',
  });

  // ---------------------- Input Handler ---------------------


  const handleInputChange = (event) => {
    const { id, value } = event.target; // Destructure event object
  
    setLanguageData((prevData) => ({
      ...prevData,
      [id]: value,
    }));
  };


  // ---------------------- form-submit Handler ---------------------

  const handleSubmit = (event) => {

    event.preventDefault();
    const myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/json");

    const raw = JSON.stringify({
      "languageId": languageData.languageId,
      "lcid": languageData.lcid,
      "codePage": languageData.codepage,
      "locale": languageData.locale,
      "languageName": languageData.languageName,
      "localLanguageName": languageData.localLanguageName
    });
    const requestOptions = {
      method: "POST",
      headers: myHeaders,
      body: raw,
      redirect: "follow"
    };

    fetch(configenv.api_host+"/api/Languages", requestOptions)
      .then((response) => {

        if (response.status != 200) {
          Swal.fire({
            icon: "error",
            title: "Oops...",
            text: "Something went wrong!",
            
          });
        }
        return response.json();
      })

      .then((data) => {
        Swal.fire({
          title: "Success",
          text: `${languageName}(${languageId}) is created..`,
          icon: "success"
        });

      })

      .catch((error) => console.error(error));

      };

```


## ---HTML--

```
  <form style={{textAlign: "center"}} onSubmit={handleSubmit}>
    <div className='row'>

      <div className='col-md-6'>

        <div className="form-group">
          <label htmlFor="languageid">Language Id</label>
          <input value={languageData.languageId} onChange={(e) => handleInputChange(e)} id="languageId" type="text" className="form-control" placeholder="Language Id"/>
        </div>

      </div>

      <div className='col-md-6'>

        <div className="form-group">
          <label htmlFor="lcid">LCID</label>
          <input value={languageData.lcid} onChange={(e) => handleInputChange(e)} id="lcid" type="text" className="form-control" placeholder="LCID"/>
        </div>

      </div>
    </div>

    <div className='row'>

      <div className='col-md-6'>

      <div className="form-group">
        <label htmlFor="CodePage">Code Page</label>
        <input value={languageData.codepage} onChange={(e) => handleInputChange(e)} id="codepage" type="text"  className="form-control" placeholder="CodePage"/>
      </div>

      </div>

      <div className='col-md-6'>

      <div className="form-group">
        <label htmlFor="CodePage">Locale</label>
        <input value={languageData.locale} onChange={(e) => handleInputChange(e)} id="locale" type="text"  className="form-control" placeholder="Locale"/>
      </div>

      </div>

    </div>              
    
    <div className='row'>

      <div className='col-md-6'>

        <div className="form-group">
          <label htmlFor="languageName">Language Name</label>
          <input value={languageData.languageName} onChange={(e) => handleInputChange(e)} id="languageName" type="text"  className="form-control" placeholder="Language Name"/>
        </div>

      </div>

      <div className='col-md-6'>

        <div className="form-group">
          <label htmlFor="locallanguageName">Local Language Name</label>
          <input value={languageData.localLanguageName} onChange={(e) => handleInputChange(e)} id="localLanguageName  " type="text" className="form-control"  placeholder="Local Language Name"/>
        </div>

      </div>

    </div> 

    <div style={{textAlign:'center'}}>
      <BasicButon label={'Add Language'} className='btn btn-outline-primary' type={'submit'} style={{height:'3rem'}}/>
    </div>
  </form>
```