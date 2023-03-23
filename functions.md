## Every function sould do just one thing
Here I have this code: 

```js
const paintSection = (section: number) => {
    console.log("sectionTemp: ",sectionTemp);
    const sectionTemp = sections[section];
    return (
      <>
        <h2>{sectionTemp.title}</h2>
        <p>{sectionTemp.desc}</p>
        {sectionTemp.questions &&
          sectionTemp.questions.map((question: any, idxQuestion: any) => {
            return (
              <div key={question.title}>
                <b>
                  {idxQuestion + 1}.- {question.title}
                </b>
                {question.idQuestionType == 1 ? (
                  <div>
                    <Form.Control
                      id={`pregunta-${question.idQuestionType}`}
                      as="textarea"
                      value={question.answer}
                      rows={3}
                      onChange={(event) => {
                        setAnswer({
                          idxQuestion,
                          section,

                          idQuestion: question.idQuestion,
                          idQuestionType: question.idQuestionType,
                          value: event.target.value,
                        });
                      }}
                    />
                  </div>
                ) : question.idQuestionType == 3 ? (
                  <div>
                    {question.options &&
                      question.options.map((option, idxOption) => (
                        <Form.Check
                          key={idxOption}
                          type={"checkbox"}
                          id={`pregunta-${question.idQuestionType}`}
                          checked={option.Opcion.checked}
                          label={option.Opcion.opcion}
                          onChange={(event) => {
                            setAnswer({
                              section,
                              idxQuestion,
                              idxOption,
                              idQuestion: question.idQuestion,
                              idQuestionType: question.idQuestionType,
                              idOption: option.Opcion,
                              value: event.target.checked,
                            });
                          }}
                        />
                      ))}
                  </div>
                ) : (
                  question.idQuestionType == 2 && (
                    <div>
                      {question.options &&
                        question.options.map((option, idxOption) => (
                          <Form.Check
                            key={idxOption}
                            type={"radio"}
                            id={`pregunta-${question.idQuestionType}`}
                            checked={option.Opcion.checked}
                            label={option.Opcion.opcion}
                            onChange={(event) => {
                              setAnswer({
                                section,
                                idxQuestion,
                                idxOption,
                                idQuestion: question.idQuestion,
                                idQuestionType: question.idQuestionType,
                                idOption: option.Opcion,

                                value: event.target.checked,
                              });
                            }}
                          />
                        ))}
                    </div>
                  )
                )}
              </div>
            );
          })}
      </>
    );
  };
 ```
